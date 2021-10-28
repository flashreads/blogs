---
id: 021-catch-and-fix-array-index-out-of-bounds-exception-in-java.md
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

We can add a try catch clouse around the code block where we are trying to access an element from an array, like in the example bellow: 

```java
public class ArrayIndexOutOfBoundsExample {

  public static int[] exampleArray = new int[10];

  public static void main(String[] args) {
    try {
      // ArrayIndexOutOfBoundsException will be thrown because
      // exampleArray only has a length of 10
      exampleVariableOne[11] = 9;
      System.out.println("Array index is valid");
    } catch (ArrayIndexOutOfBoundsException e) {
      System.out.println("Array index is out of bounds");
    }
  }
}
```


Another ways to prevent `ArrayIndexOutOfBoundsException` is to maintain or control the count in the loop of an array. Check this 3 exampes: 


```java
public class ArrayIndexOutOfBoundsExample {

  for(int count = 0; count < array.length; count++) {
    System.out.println(array[count]);
}
```

```java
int count = 0;
while(count < array.length) {
    System.out.println(array[count]);
    count++;
}
```

The best way to prevent ArrayIndexOutOfBoundsException is to use for-each loop where we don`t have to worry about the count.

```java
for(String str : array) {
    System.out.println(str);
}
```

So next time make sure that you double check your code and prevent `ArrayIndexOutOfBoundsException`.  
