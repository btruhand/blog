---
layout: post
description: Lessons from using mocks in software testing
title: Re-thinking Mocks
categories: [java, TDD, software]
permalink: /post/:year/:month/:day/:title
toc: true
---

These days I have mainly been using Java for my professional career (roughly I have been working with Java for a year). I also mainly have been using the
[Spring framework](https://docs.spring.io/spring/docs/current/spring-framework-reference/) along with its additional libraries at work. One of the things that
I enjoy with Spring is the dependency injection capability that it provides, primarily through the `@Autowired` annotation. This quick and easy way to do dependency
injection is also further compounded in testing benefits as Spring also provides easy and seemless way to obtain these dependencies at test time (`@Import` and
`@ContextConfiguration` to name a few) makes testing much easier. I also make a good amount of use [Mockito](https://site.mockito.org/) which makes my development
life much easier through `mocks`, and this post is about `mocks` and my experience and thoughts on them.

# What are mocks

This question has been covered in a variety of other posts out there, one of which I found most useful to be [Martin Fowler's post](https://martinfowler.com/articles/mocksArentStubs.html). In the words of Martin Fowler himself:

> Mocks use behavior verification, where we instead check to see if the order made the correct calls on the warehouse. We do this check by telling the mock what to expect during setup and asking the mock to verify itself during verification

At the heart of mocking is behaviour verification, which is the ability to assert what has **happened** during the execution of a test, and not just what the system
under test has produced. Martin Fowler made a clear distinction and emphasis on this part which you can read up on his post.

# Quick example

```java
class ClassA {
    ClassB dependency;
    boolean shouldDoFunc;

    ClassA(ClassB dependency, boolean shouldDoFunc) {
        this.dependency = dependency;
        this.shouldDoFunc = shouldDoFunc;
    }

    void func() {
        if (this.shouldDoFunc) {
            this.dependency.doFunc();
        }
    }
}

class ClassB {
    void doFunc() {
        // do something
    }
}

// test code below
void test_func_whenShouldNotDoFunc_notCallDoFunc() {
    ClassB classB = mock(ClassB.class);
    ClassA classA = new ClassA(classB, false);

    classA.func();
    verify(classB, never()).doFunc();
}
```

The above example is extremely contrived but it just barely shows the use case of mocks. The call to the `verify` function says that we are trying to verify
that when `shouldDoFunc = false`, we expect that `ClassB.doFunc` will not be called.

The alternative to using mocks above would be to supply an actual instance of `ClassB` (not mocked) and check against the *results* after calling `ClassA.func`.
Now in the above example no values are being returned from any of the function calls so no returned value can be expected, however often such functions causes
side-effects. Common side-effects include calling some API that causes some change, changing the environment settings, performing DB changes such as updates, changing
the state of `ClassB` and many more. Such side-effects are testable and verifiable (if there are no side-effects performed by the function I question why the function
exists).

# The positives of mocks

From my experience thus far using mocks is that it has been beneficial to create tests. Certain testing may require an expensive setup or verification procedure,
which makes tests run slow but also developed more slowly. An alternative to mocks may include creating fakes or stubs (a separate kind of testing entity), which may
also create additional development effort to make and also may require its own maintenance. Though a great deal of this benefit comes from the fact that many languages
have a well-tested and prevalent mocking library.

Mocks also makes creating truly `unit` tests easier, and by unit here I mean tests that only put a single class/object under test. Mocks enable me to put the focus
and attention of tests on the specific unit under test and not have to worry about the other interacting pieces. In the example above, the test is made deliberately
about `ClassA.func` behaviour when it is in a certain state. In more complex objects under test, this makes some desired fine-grained testing much more approachable
and manageable.

# The negatives of mocks

The biggest drawback using mocking is it requires whitebox testing, in order to verify using mocks we need to know what functions are being called, which essentially
bears down to knowing some level of detail about the implementation of the unit under test. Nowadays I think of this as *reflection for testing*. Reflection is the
ability to inspect programming constructs at runtime of some code within the code itself. Often this involves passing in names of functions or fields in the form of
strings to specialized reflection APIs. Since access is made via strings, IDEs won't help you during refactoring which makes mistakes during changes in the codebase
harder to detect. Thankfully a testing is one of the tools we have to safeguard ourselves against our programming mistakes, until the tests start to fail us.

Using reflection capabilities requires the programmer to have clear knowledge about what is and isn't present and bake that knowledge statically into the code and
it is the same case when we use mocks. Now libraries like `Mockito` does enable the use of refactoring through IDE unlike reflection, but mocking doesn't easily
allow us to change the tests when the dependency calls in the code under test changes. This creates a mismatch between expectation and reality. For example, if in
`ClassA` above we change the call of `doFunc` to another function `doFunc2`, the test would still pass but for very much the wrong reason! The reality is that
`doFunc` is no longer a dependency call being made, but the test still expects it as a call to be made and it just so happens the test was verifying that no calls
were to be made. The following test would fail:

```java
void test_func_whenShouldDoFunc_callDoFunc() {
    ClassB classB = mock(ClassB.class);
    ClassA classA = new ClassA(classB, true);

    classA.func();
    verify(classB, once()).doFunc();
}
```

but now the test fails for the wrong reason! The test will fail because the test is expecting the wrong thing, not because the unit under test is behaving
incorrectly. This is test maintenance drag. Martin Fowler calls this the coupling of implementation and testing.

# An alternative for mocking

One of the compelling alternatives to mocking is by supplying functions as parameters to the unit under test instead of whole object dependencies. The ability to pass
functions as parameters is called [First-class function](https://en.wikipedia.org/wiki/First-class_function). Consider this example in pseudo-Javascript 

```javascript
function funcToTest(dependentFunction) {
    if (some condition) {
        dependentFunction();
    }
}

test_funcToTest_whenConditionNotMet_doNotCallDependentFunction() {
    // do something to cause condition to not be met
    counter = 0
    funcToTest(() -> counter + 1)
    if (counter != 0) {
        throw new TestFailed()
    }
}
```

The passed in `dependentFunction` is simply a function passed as a parameter that is called when some condition is met inside `funcToTest`. Notice how in the test we
are also verifying the behaviour of `funcToTest` under some condition, similar to the example with `ClassA`. In both the test using mocks and first-class function we
see that behaviour is being verified, and this should come as no surprise. We can think of objects as instances of namespaces/groupings for functions (with the ability
to maintain and collect some form of internal state) and so when we pass an object as a dependency it can be seen as passing in a collection of functions. The
difference is that when we use mocks we have to explicitly mention the dependent function we are interested in, while with first-class functions the dependent function
is stipulated in formal syntax (scratching off the fact that it's possible to call functions without their parameters in Javascript). With mocks tests can fail/pass
for reasons of a mismatch between expectation and reality, with first-class functions that possibility is greatly diminished and if it happens is likely the
programmer's mistake.

However in reality I have not used first-class functions as an alternative to mocks at all. Much the reason is because it is much easier to work with objects and
mocks in Java. Though Java does have lambda functions and the [@FunctionalInterface](https://docs.oracle.com/javase/8/docs/api/java/lang/FunctionalInterface.html)
it is not that fluid to create classes and methods that take in first-class functions all the time. But this is surely a technique that I would explore and be more
conscious of in the future.