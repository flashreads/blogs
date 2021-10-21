---
id: 016-catch-and-fix-null-pointer-exception-in-java.md
title: Catch and fix NullPointerException in Java
tags:
  - nullpointerexception
  - exception
  - runtimeexception
author: Kosta Lazarevski
meta-description: Learn how to catch and fix NullPointerException in Java
keywords: exception, nullpointerexception, javaruntimeexception
template: post
categories:
  - java
  - exception
---

## What is a NullPointerException?

`java.lang.NullPointerException` is a runtime exception in Java. It occurs when a variable is accessed which is not pointing to any object and refers to nothing hence it is null.

Since the `NullPointerException` is a runtime exception, it doesn't need to be caught and handled explicitly in application code.

## What are the reasons for getting NullPointerException?

The `NullPointerException` occurs due to a situation in where an uninitialized object is attempted to be accessed. This means the object reference does not point anywhere and has a null value.

Some of the most common scenarios for a NullPointerException are:

#### Accessing a null object’s properties
#### Throwing null from a method that throws an exception
#### Incorrect configuration for dependency injection frameworks ex:(Spring)
#### Passing null parameters to a method
#### Calling methods on a null object
#### Using synchronized on a null object
#### Accessing an index element (like in an array) of a null object


## Example of a NullPointerException

In this example we are trying to call a printLength methos which accepts a String as a parameter and prints its length. If the value of the String that it is passed as a parameter is null,
a java.lang.NullPointerException will be thrown.

```java
public class NullPointerExceptionExample {
    private static void printLength(String str) {
        System.out.println(str.length());
    }

    public static void main(String args[]) {
        String nullString = null;
        printLength(nullString);
    }
}


Exception in thread "main" java.lang.NullPointerException
    at NullPointerExceptionExample.printLength(NullPointerExceptionExample.java:3)
    at NullPointerExceptionExample.main(NullPointerExceptionExample.java:8)
```

## How to Avoid getting NullPointerException

The `NullPointerException` can be avoided using checks and preventive techniques like the following:

Making sure an object is initialized properly by adding a null check before referencing its methods or properties.

Using Apache Commons StringUtils for String operations e.g. using StringUtils.isNotEmpty() for verifying if a string is empty before using it further.

```java
import org.apache.commons.lang3.StringUtils;

public class NullPointerExceptionExample {
    private static void printLength(String str) {
        if (StringUtils.isNotEmpty(str)) {
            System.out.println(str.length());
        } else {
            System.out.println("This time there is no NullPointerException");
        }
    }

    public static void main(String args[]) {
        String nullString = null;
        printLength(nullString);
    }
}
```

Using primitives rather than objects where possible, since they cannot have null references e.g. using int instead of Integer and boolean instead of Boolean.

So next time make sure that you double check your code and prevent `NullPointerException`.  
