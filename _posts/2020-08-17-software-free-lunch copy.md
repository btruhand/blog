---
layout: post
description: Learning that Spring's RestTemplate buffers request body under certain situations, which leads to unexpected errors
title: Request Body Buffering With Spring's RestTemplate
categories: [technology, java, spring, springboot]
permalink: /post/:year/:month/:day/:title
ril: true
toc: true
---

# Background

I have been using the Java Spring framework for my work for a while now. I started learning the Spring framework while building a REST API application which had to connect to other remote services through their own REST API interface. While the [Spring RestTemplate](https://docs.spring.io/spring/docs/current/spring-framework-reference/web.html#webmvc-client) is currently only in maintenance mode and expected to be deprecated completely in the future, it was the first thing that I found for making HTTP requests in the Spring framework. So I just started using it out of practicality.

Now we often want to make log HTTP requests our servers make. One way is to put log statements everywhere we needed to make HTTP calls. One of the alternatives with Spring RestTemplate is to configure a [logging interceptor](https://www.baeldung.com/spring-resttemplate-logging#logging-body-with-a-resttemplate-interceptor). This way we can configure a global (or several) RestTemplates that have configured logging capability.

```java
public class LoggingInterceptor implements ClientHttpRequestInterceptor {
	 
	    static Logger log = LoggerFactory.getLogger(LoggingInterceptor.class);
	 
	    @Override
	    public ClientHttpResponse intercept(HttpRequest req, byte[] reqBody, ClientHttpRequestExecution ex)
	      throws IOException {
	        log.debug("Request body: {}", new String(reqBody, StandardCharsets.UTF_8));
	        ClientHttpResponse response = ex.execute(req, reqBody);
	        InputStreamReader isr = new InputStreamReader(response.getBody(), StandardCharsets.UTF_8);
	        String body = new BufferedReader(isr)
	          .lines()
	          .collect(Collectors.joining("\n"));
	        log.debug("Response body: {}", body);
	        return response;
	    }
	}
```

Taking from the Baeldung post above, we can see that the signature for the `intercept` method contains a `reqBody` parameter of type `byte[]`. This means that in order to log the outgoing request body, Spring has to serialize whatever we are sending to a byte array structure in-memory. Depending on the request body that you are sending this can cause memory issues, and perhaps even out of memory errors. Additionally it probably has performance impact to your application, even if a little. So it's something that may need some considerations.

# The problem

Now in my current project I have to relay uploaded files made by clients to another service through its API call. These files will potentially be in gigabyte size range. Still using RestTemplate I realize immediately that the application will run out of memory if I logged using the interceptor above. So I decided to create two kinds of RestTemplate, one that can is configured to log requests automatically and another that doesn't. Additionally I used [HttpComponentsClientHttpRequestFactory.setBufferRequestBody(false)](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/http/client/HttpComponentsClientHttpRequestFactory.html#setBufferRequestBody-boolean-) to ensure that the application will not buffer the uploaded file that needs to be relayed.

But when I was functionally testing the application I kept running to out of memory errors when uploading a 1.5 GB file and no matter what I did I could not fix it. After investigating further it turns out that I didn't know the [SpringBoot Actuator](https://docs.spring.io/spring-boot/docs/current/reference/html/production-ready-features.html) is available in the classpath. One of the things that the Actuator package provides is metric collection of outgoing HTTP clients made by RestTemplates, which is automatically provided if we build our `RestTemplate` through the auto-configured `RestTemplateBuilder` provided by SpringBoot. That is if we created our RestTemplate like the following:

```java
@Bean
public RestTemplate restTemplate(RestTemplateBuilder builder) {
    return builder.build();
}
```

then the metric collection capability is automatically configured. And of course the metric collection is done by adding an interceptor, to be precise the [MetricsRestTemplateCustomizer](https://github.com/spring-projects/spring-boot/blob/master/spring-boot-project/spring-boot-actuator/src/main/java/org/springframework/boot/actuate/metrics/web/client/MetricsClientHttpRequestInterceptor.java) is used. This interceptor is added to the `RestTemplateBuilder` I used above to build the `RestTemplate`, and therefore all of my requests made with the `RestTemplate` that wasn't configured for logging was actually buffering the request body! No wonder I kept hitting OOM errors...

# The fix

Well the fix is actually quite simple, I just built the `RestTemplate` without the configured `RestTemplateBuilder` provided and everything is fine! Well... in the end I decided to move the application to use [WebClient](https://docs.spring.io/spring/docs/current/javadoc-api/org/springframework/web/reactive/function/client/WebClient.html) instead. Not only it is the suggested API to use now, thus am building for a future proof application, I would still be able to log requests without having to be forced to buffer the request body. Though if I want to log the request body programmatically, I would still be required to buffer the request body, but that's a separate issue for the future.