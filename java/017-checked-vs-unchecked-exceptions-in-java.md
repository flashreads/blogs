---
id: 017-checked-vs-unchecked-exceptions-in-java.md
title: Checked VS Unchecked eceptions in Java
tags:
  - checked
  - unchecked
  - exception
  - runtimeexception
  - error
author: Kosta Lazarevski
meta-description: Learn the difference betwen checked and unchecked exceptions in Java
keywords: exception, checked, javaruntimeexception, unchecked, error
template: post
categories:
  - java
  - exception
cover: ../../images/categories/java.png
---




## Checked versus Unchecked Java Exceptions
### We can devide Java exceptions into three categories:

**Errors** and **Exceptions** can be frustrating at times, but at the end of the day we need to know how to solve them. That is what we do. This little blog will help you learn about the types of Java Exceptions and they mean.
These three categories are broken down into checked and unchecked classifications—error and runtime exceptions. Errors and Runtime Exceptions are classified as an unchecked, which means are not checked at compile time and can result in runtime errors.


**Checked** - these are exceptions that are checked by the compiler at compile time. These exceptions must be caught by a try/catch in the code or noted as thrown by the method. For instance, if a program attempts to access a file that is currently unavailable, the method to access the file must either catch or throw a `FileNotFoundException`.

**Error** - errors are exceptions that happen externally to your Java program. One common example of the error is when the Java virtual machine (JVM) runs out of memory, which will throw an `OutOfMemoryError`.

**Runtime** - runtime exceptions are internal to your application but are not typically recoverable. For example, an object that is expected to have a value but is actually null. In this case, a `NullPointerException` exception would be thrown.

These three categories are broken down into checked and unchecked classifications—error and runtime exceptions and are grouped together as unchecked, which, per their name, are not checked at compile time and can result in runtime errors.
