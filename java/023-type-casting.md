---
id: 023-type-casting
title: Type Casting
tags: 
- java 
- object 
- type
date: 2021-10-31 16:08:39 
keywords: java, object, type
categories: 
- java
cover: ../../images/categories/java.png
author: Ryan Omoruyi
meta-description: Type Casting in Java
---

# Type Casting

Type casting is when the data type of a variable is casted to another type. There are two types of casting: Widening and Narrowing.

## Converting a Variable's Type Using Widening Casting 
With this type of casting, there is no extra code that needs to be written. Java does this for you under the hood when a smaller type is converted to a larger type. When dealing with numbers, a `byte` is the smallest data type (whole numbers from -128 to 127), then a `short` (whole numbers from -32,768 to 32,767), `int` (whole numbers from -2,147,483,648 to 2,147,483,647), `long` (whole numbers from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807), `float` (fractional numbers with 6 to 7 decimal places), and `double` (fractional numbers with 15 decimal places).

```java
    int intType = 2021;
    // casting at assignment
    float floatType = intType; // Outputs 2021.0
```

## Converting a Variable's Type Using Narrowing Casting
This casting is used when converting from a larger data type to a smaller type. For example, converting from a `long` to an `int` requires Narrowing casting. For example:

```java
    long longType = 2000000L;
    // Cast by wrapping the desired type in parentheses before the value
    int intType = (int) longType; // Outputs 2000000

    // won't work if the long value is greater or less than int's range
    longType = 3000000000L; // greater than the upper limit of int type
    // the data is cast to an int
    // since the long value is out of int's range, Java tries converting to a value within range
    intType = (int) longType; // Outputs -1294967296
```

## Typecasting WYNTK

Typecasting doesn't work for all data classes. Some may wonder if you can convert a `char` to a `String` and vice versa. Primitive data types are the only data types that can be casted in this manner. And since the `String` class is not a primitive type, it's not allowed. There are, however, built in methods in the String class that help do this; like the `String.valueOf(char c)` method and in the Character class like `Character.toString(char c)`.

