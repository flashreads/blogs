---
id: 020-errors-in-java.md
title: Errors In Java
tags:
  - java
  - errors
  - exception
author: Nisarga K H
meta-description: Learn about common errors and its types in Java
date: 2021-10-27 21:08:32 +0530
keywords: java, errors, exception
template: post
categories: 
    - java
cover: ../../images/categories/java.png
---

# ERRORS

`Error` results in abnormal working of the program. Some errors dont let the program to be compiled meanwhile some errors occur during execution after succesful compilation. Based on this factor errors are classified into three main types.

## Types Of Errors

There are three types of errors in Java

1. Syntax errors
2. Logical errors
3. Runtime errors (Exception)

### 1. Syntax errors

These are the errors which occur when our compiler finds violation of Java syntax in our program. It is also called as compile time error as it is detected by the compiler.

Example:
```java

public static void main(String args[]){

    //Semicolon missing

    int a=9   // semicolon missing
    int b=3+a;

    System.print.println(b);

    // Datatype missing

      d=3456;

}
```


### 2. Logical errors

These are also called as bugs. This occurs when the program compiles and runs but the expected output is not received when certain input is given. These happen due to not using appropriate logic in the program by the user.

Example:

```java
public static void main(String args[]){
    
    // Find product of a and b
    int a = 34;
    int b=0;

    
    int c= a/b;

    System.out.println("product of a and b is"+c);

    //But here c is the quotient not the product of a and b
}
```


### 3. Runtime errors

These errors are encountered while the program is executing. They get successfully compiled but throw an exception while running. These are also called `Exceptions`. They are hard to find as compiler doesnt point at the line where the error as ocurred.

Example:

```java
public static void main(String args[]){
    
    //Number divided by 0 is not defined
    int a = 34;
    int b=0;

    int c= a/b;

    System.out.println(c);
}
```