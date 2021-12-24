---
id: 022-catch-and-fix-array-index-out-of-bounds-exception-in-java.md
title: Catch and fix ArrayIndexOutOfBoundsException in Java
tags:
  - arrayoutofboundsexception
  - exception
  - runtimeexception
  - java exception
author: Kosta Lazarevski
meta-description: Learn how to catch and fix ArrayIndexOutOfBoundsException in Java
keywords: exception, arrayoutofboundsexception, javaruntimeexception
template: post
categories:
  - java
  - exception
image: assets/images/fix.svg
---

## What is a ArrayIndexOutOfBoundsException?

`java.lang.ArrayIndexOutOfBoundsException` is a runtime exception in Java. occurs while processing an array and asking for a position that does not exist within the size of the array.

Since the `ArrayIndexOutOfBoundsException` is a runtime exception, it doesn't need to be caught and handled explicitly in application code.

## Example of a ArrayIndexOutOfBoundsException

In this example we are trying to access an element at index 5 of the animals array, which has only 2 elements. In this case java.lang.ArrayIndexOutOfBoundsException will be thrown.

```java
public class ArrayIndexOutOfBoundsExample {
  public void processArray() {
    List animals = new ArrayList<>();
    names.add("cat");
    names.add("dog");

    return animals.get(5);
  }
}
```

## How to Avoid getting ArrayIndexOutOfBoundsException

The `ArrayIndexOutOfBoundsException` can be avoided using checks and preventive techniques like the following:

1. Always remember that the array is a zero-based index, the first element is at the 0th index and the last element is at length - 1 index.
2. Pay special attention to the start and end conditions of the loop.
