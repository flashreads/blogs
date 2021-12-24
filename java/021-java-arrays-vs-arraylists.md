---
id: 021-java-arrays-vs.arraylists.md
title: Arrays vs. ArrayLists in Java
tags: 
 - java
 - arraylists
 - arrays
author: Cindy Li
meta-description: Learn about the differences between Arrays and ArrayLists in Java
date: 2021-10-30 22:10:31 
keywords: java, arraylists, arrays
template: post
categories: 
  - java
image: assets/images/java/java8.svg
---


# Arrays vs. ArrayLists
Although 'arrays' and 'Arraylists' both store information in the form of lists, one of the most fundamental differences between the two is how an array is a 'fixed legnth data structure' while an Arraylist is a 'variable length Collection class'. This means that the legnth of an array cannot be cahnced after being created, but the legnth of an Arraylist can. In addition, since ArrayList implements the Collection interface, it can only store 'objects', whereas arrays can store both 'objects' and 'primitives' such as int, boolean, char, etc. To make an ArrayList of integers, for example, we would need to convert integers into an object. 


# Declaring Arrays
There are two ways to declare and initialize arryas:

  ## 1) Declaring and initializing at the same time
Example: 
```java

public static void main(String args) {

  int[] numList = {1, 2, 3, 4, 5, 6, 7};
  
}

```

Here, the declaring part - which declares the type and name of the array - and the initializing part - which initializes the elements in the arrays - are combined into one line. 

  ## 2) Declaring then initializing later
Example: 
```java

public static void main(String args) {
  
  int[] numList = new int[7];
  numList[0] = 1;
  numList[1] = 2;
  numList[6] = 7;
  
}

```

Here, we first declared the type, name, and length of the array. Then, initialized by assigning a value to each index of the array. 


# Declaring ArrayLists
Like declaring arrays, there are multiple ways to declare ArrayLists as well

## 1) Initialization with add()
Example: 
```java

public static void main(String args) {

  ArrayList<String> example = new ArrayList<String>();
  
  example.add("this");
  example.add("is");
  example.add("an");
  example.add("example");
 
 }
 
 ```
 Here, we first created the ArrayList with the type (String) and the name (example). Then, we initialized the elements with add().
 
 ## 2) Initialize using asList()
 Example: 
 ```java
 
 public static void main(String args[]) {
 
  ArrayList<String> example = new ArrayList<String>(
    Arrays.asList("this", "is", "an", "example"));
    
}

```
Here, the ArrayList is declared and initialized all at once by initializing the Strings using asList(). 

## 3) Initialize using List.of()
Example:
```java

public static void main(String args[]) {

  List<String> example = new ArrayList<>(
    List.of("this", "is", "an", "example"));
    
}

```
List asList(), this method declared and initialized the ArrayList all at once.
