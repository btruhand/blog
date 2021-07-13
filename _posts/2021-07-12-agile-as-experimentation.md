---
layout: post
description: In this post I posit that the heart of Agile is scientific experimentation and not any of the marketed Agile methodologies like Scrum, Kanbdan etc.
title: Agile is Experimentation
categories: [software development, management, organizational techniques]
permalink: /post/:year/:month/:day/:title
toc: true
---

Recently I had a conversation with two gents about software development and the word "Agile" propped up. As software engineers, or even business management these days, the word agile is everywhere. In job postings, in company slogans, in company talks, on our computer screens, and in our purported work values. But I know from personal feelings, observations and anecdotes there is some distaste to "Agile" and that it feels more as hype and even worse at times feels like a marketing tool to attract talent which sadly does not deliver.

So as per my usual inquiring-and-chatty-self I asked the two gents, "So, what does agile mean to you?". And I purposefully directed the question to them through the vocabulary "you" because I want to understand their own personal mental model of Agile. I do not care about Scrum, Kanban or whatever new Agile framework out there is, I wanted to get to the fundamental of Agile.

The first said that for him Agile is all about doing breaking up the work and taking them up. He stated that the importance is not in the pointing mechanism itself, but more in actually being able to take up and do the work. The other said that Agile for him is all about the small iterative steps that is aimed for continuous refinement.

I think these kind of mental models of Agile is quite common. Generally they are surmised by these adjectives or nouns: 'iterative', 'small', 'continuous improvement'. But I would like to further refine this understanding of iteration. So let's do that in this post, let's try to develop a better mental model of Agile.

Here is my take:

> The main abstraction provided by Agile is experimentation

# Experimentation first, the rest is by-product

As software engineers we love to abstract things away, to turn details into common patterns that can be encoded as a set of computer interactions (algorithms basically) to solve a problem, or class of problems. As a software engineer I posit that the main abstraction that Agile brings is experimentation in order to solve the problem of business development and innovation.

And when I say experimentation, I really mean experimentation as in the scientific method sense:

<figure>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/82/The_Scientific_Method.svg/1024px-The_Scientific_Method.svg.png">
    <figcaption>A picture of the scientific method, which is an on-going process. Source - <a href="https://en.wikipedia.org/wiki/Scientific_method">Wikipedia</a>
    </figcaption>
</figure>

Since I posit that Agile is really all about experimentation brought to business practice, then there are four elements that businesses adopting Agile must absolutely meet:

1. A hypothesis to test
2. Mechanisms to perform tests for or against the hypothesis
3. The gathering of, and capability to assess data
4. A commitment and understanding to learn and adapt continuously based on feedback of previous experiments

When viewing and applying Agile as experimentation through the scientific method towards business, iteration and continuous improvement is a given. It simply becomes a by-product. Small requires an additional perspective which I will touch later on, but I assure you that it remains a by-product.

# On hypotheses and testing

Now I would like to touch on hypothesization and testing because as a software engineer this is where a lot of software engineer's time is spent struggling on. It shouldn't and definitely isn't the only phase in the Agile cycle where software engineers are involved in, but I find a lot of software engineers along with their business counterparties stumble in these areas often. The stumbles that occur here impede the whole Agile flow, and impacts its adoption within a team and potentially organization at large.

## Poorly made hypotheses

The development of the hypothesis is often estranged from the software engineers' work and by that I mean something like the following:

> Business asks for a feature > Business comes up with requirements > Business forks over requirements to engineers

There are two problems with this kind of "hypothesization":

1. It isn't really framed as a hypothesis. A hypothesis is about creating an assumption that is meant to be further investigated. Hence a hypothesis must always be made with the presupposition and even expectation that it may be false or incorrect. So a rewording may say that "Business thinks that a feature would be useful to be developed" instead. [Dave Farley in his video](https://youtu.be/eozFlgu6ByY) covers this idea of expecting false assumptions further and better than I do
2. The software engineers are often the people who procure the experimentation "ingredients" (code and machineries) and make the testing of the hypothesis possible. When the those that are creating the test experiments are not involved in the development of the hypothesis, there is significant risk that what would be setup does not reflect what the hypothesis is claiming. In other words - what software engineers develop may stray away tremendously from what the business actually needs

## Failure to perform tests for the hypothesis

Assuming that the software engineers have managed to scrounged up some code for the hypothesis, Agile as experimentation would say the next step is to test that the hypothesis is correct. You can also say you can (and probably should) test that the implementation of the hypothesis is correct. But too many organizations forego this step, likely because they do not think of Agile as experimentation. The result of this in my experience usually leads to (in order of severity and face-palm worthiness, with some embellishment):

1. Never testing it because the software never got released in fear of what can go wrong (and also not knowing what can go right)
2. Letting the majority of the users be the one and only tester of the hypothesis - it's not a bug, it's a feature (or it's not a feature, it's a bug)
3. Business performs tests on their side only at the very end when every hypothesis are realized as code. Then they spectacularly notice that nothing works as hypothesized
4. Software engineers never testing out their code and solution before running experiments. Usually exacerbating the length of feedback loops and by the time they are aware of issues highlighted in experiment results they already forgot what they did
5. Silo'd QA teams that have no idea what is happening and have poor awareness of the hypothesis that needs to be tested

The lack of testing, and the inability to perform testing whether because of technological unreadiness or organizational politics impedes the collection of data. Without this data, Agile breaks down because the next experiment cycle will be disconnected from the previous. And even if the next experiment cycle does not have anything to do with the previous one, without testing the experiment cycle is incomplete. Yet many teams and businesses readily jump in to the next experiment without really finishing the previous one at all.

It must be noted that the procurement of data and testing of the hypothesis in Agile may come from various tests and groups of testers. This idea of diverse testers should be intuitive in both its concept and also importance. In fact, the differing kinds of testers at times also help keep the experiment iteration small. For example, software engineers as testers is likely (or hopefully) testing a small piece of the hypothesis in a fairly quick manner, keeping the experiment and feedback fast and small.

# Failures in adopting Agile

Now that we've postulated Agile as primarily an experimentation it becomes we can look at the potential concrete reasons why Agile adoption fails. And here is where the pscyhology aspect of working with or within Agile becomes more prominent.

## Mischaracterization of Agile

The first thing that is quite likely to have happened is that the organization has mischaracterized Agile as a set of procedures and formal methodologies. This is exactly not what Agile was meant to be based on the Agile manifesto. The focus is likely to have been aimed at adopting Scrum or Kanban methodologies while missing the essence of Agile; an abstraction for scientific experimentation for the business problems.

## Closing off from being wrong

If you watched Dave Farley's video that I linked above you should understand where I am coming from with this. Experimentation necessitates that there is an uncertainty that wants to be further investigated. By nature this must mean that incorrect hypothesis and even seemingly unfruitful effort will be made as business attempt to solve problems through products, services and processes.

The idea of being wrong is psychologically difficult to reconciliate with. There is also a social dimension to it which hits some people harder than others, for legitimate and illegitimate reason. But even disregarding that, our brain and ego often limits our ability to accept mistakes, by others or ourselves. 

## Inability to change

The scientific method is a continuous loop. Each loop may feed in new data points and observations for the next loop. Iteration is enabled by the successive feed of data from one step to another. But some experiments will inevitably challenge our assumptions and hence our cycle. More likely though, challenges will come from external sources Agile processes. It is unlikely that your Agile journey will be a sequence of smooth loops; they say the only constant is change.

Disregarding turbulent external change, Agile itself promotes change, and so it must be something that teams and organizations can work and be comfortable with. But inherently change is difficult to do. There is technical aspect of change which is difficult in itself which covers aspects of software design, architecture, CI/CD and many more. Then there is the fragility of our human cognition in accepting change.

The need for change may be brought by previously held incorrect hypothesis or experimentations. And we've said that accepting being wrong in itself is already hard. Even if it isn't necessitated by previous missteps we may be prone to a [status quo bias](https://en.wikipedia.org/wiki/Status_quo_bias). Or perhaps we have a [sunk cost fallacy](https://www.behavioraleconomics.com/resources/mini-encyclopedia-of-be/sunk-cost-fallacy/) towards our previous assumptions. Erroneously, some organizations may situate themselves to be unable to respond to the need for change because of an [end-of-history illusion](https://en.wikipedia.org/wiki/End-of-history_illusion)

## Uncontrolled change

Some organizations do change, to the point of being overwhelmed by change. Change is difficult, and more so when change happens frequently and in an unstructured fashion. The COVID-19 pandemic has thought us that we need to change our long-held practices. But the deluge, abrupt and perhaps unprecedented scale of change that needs to be adapted for the modern era made many of us grind to a halt.

Here are some examples of our difficulty when change is uncontrolled:

- Small businesses anguish at ever changing regulations and response turbulence
- Health officials saying they are doing science by looking and listening to the evidence that is constantly changing based on new data points. To many it seems these officials are flip-flopping and changing their stance or suggestions.

Scrum, Kanban and other Agile methodologies particularly shine here by bringing in a framework that acts as a guidance. In particular the emphasis on the dissection of experiments into smaller pieces helps to make change feel and be manageable. But these methodologies work best when the change being brought are iterative towards some form of north star, a loose trajectory guidance. When the north star itself is what keeps changing, many will find it difficult to handle what often becomes uncontrolled change.

## Industrial friction

Assuming that individuals within the organization themselves can apply Agile as a way of experimentation, there are still industrial challenges to the adoption of Agile. Such challenges may come internally or externally.

Internally, the problems mentioned above can equally be replicated and exacerbated on the organizational level. So there are the pscyhological dimensions on the individual and corporate that needs to be addressed in the adoption of Agile. Many organizations are still not comfortable yet in performing experiments; in hypothesizing, testing, analyzing data and rinse and repeat. They view business problems as work that needs to be steamrolled in one go.

Externally, some organizations are situated within an industry that makes experimentation difficult. These industries often have low tolerance for mistakes. Arguably all industries are intolerant for mistakes, but some just feel more daunting than others, whether that is true or not is another topic.

Despite internal or external friction, it is possible to adopt Agile methodologies in gradients. While indeed Agile can be adopted within the context of "move fast and break things", it can also be adapted in more nuanced and smaller scale. I take inspiration from SpaceX that continuously runs launch experiments against their hypothetical products. The level of funding needed to run these experiments, which may end with million-dollars fireworks, is ludicrously high. Yet, SpaceX shows that it is possible that Agile is possible even in high-stake.

So instead of fully backing off from Agile, we can try to see at which parts of our organizations do Agile make sense and in what form. At the very least I think all software engineering teams can and should adopt Agile by adopting CI/CD pipelines.

**NOTE**: Dave Farley has a [video](https://youtu.be/v8f6q4ruvds) more on SpaceX.

# Final comments

When I hear Agile, I always think of the [Agile Manifesto](https://agilemanifesto.org/). We know that at the heart of it Agile is not Scrum, and it is not Kanban. I posit it as the abstraction of the scientific experimentation to solve business problems.

Seeing Agile as experimentation puts a lot of emphasis on `Working software` and `Responding to change` of the Manifesto. In particular, the Agile experiments are there to serve as a way to create software that works (for customers, not just for computers) according to battle-tested hypotheses. The experimental loop fundamentally necessitates organizations to expect change from the Agile cycles, and also from external forces.

Hopefully this helps you in truly bringing Agile changes to your organization.
