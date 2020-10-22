---
id: 004-difference-between-@Controller-and-@RestController-in-spring-boot.md
title: @Controller vs @RestController in Spring Boot
tags: java, spring boot, controller, annotation, mvc, rest
author: Kosta Lazarevski
meta-description: Learn how to define your controller classes in spring boot mvc
---

# @Controller vs @RestController

The @RestController annotation in Spring MVC is a combination of @Controller and @ResponseBody annotation. It was added into Spring 4.0 to make the development of RESTful Web Services in Spring framework easier. If you are familiar with Rest web services you know that the main difference between a web application and REST API is that the response from a web application is view in HTML + CSS + JavaScript (client/human view), 
While REST API returns data in form of JSON or XML(most of the REST clients are programs) From there we can see the difference between @Controller and @RestController

@Controller creates a map of the model object and finds a view. @RestController returns the object and object data written onto HTTP response as JSON or XML.

The traditional way is to use @Controller and use @ResponseBody annotation but since this is the default behavior of RESTful Web services, Spring introduced @RestController which combined the behavior of @Controller and @ResponseBody together.

Here is an example of a code snippets with the same functionality:


```java

@Controller
@RequestBody
public class MvcController { 
   .. your logic
}


@RestController
public class RestFullController { 
  .... your logic
}

```

The @Controller annotation indicates that the class is a "Controller" like a web controller while @RestController annotation indicates that the class is a controller where @RequestMapping methods assume @ResponseBody semantics by default i.e. servicing REST API.

The @Controller is a specialization of @Component annotation while @RestController is a specialization of @Controller annotation. It is actually a convenience controller annotated with @Controller and @ResponseBody. 
