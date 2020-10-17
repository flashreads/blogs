---
id: 006-set-interface-in-java.md
title: Set interface in Java
tags: java, collection, set, hashset, treeset, linkedhashset
author: Kosta Lazarevski
meta-description: Learn how to use Set interface to store, manipulate data in Java
---


# Set Interface

The Set Interface `java.util.Set` represents an unordered list of elements(objects). Set Interface can store only unique values, that means that you can not have duplicates in Set. `Set` interface is implemented by the classes `HashSet`, `LinkedHashSet`, `TreeSet`(this class implements the `SortedSet` Interface). Set has many methods to add, remove and manipulate data.

## HashSet

`HashSet` class stores elements in a hash table, and it is best performing implementation of the `Set`. It does not guarantee the order in which elements are inserted. `HashSet` allows `null` values but can not contain duplicate values. Internally uses a `HashMap` to store the elements. 

Example:

```java

import java.util.HashSet;
import java.util.Set;

public class HashSetExample{
  public static void main(String [] args){
     
     //Creating a HashSet
     Set <String> names = new HashSet<String>();

     //Adding new elements to the HashSet
     names.add(“Mike”);  
     names.add(“Bob”);
     names.add(“Maria”);
     names.add(“Karen”);
     names.add(“Mike”);

     System.out.println(names);

     //Removing an element of the HashSet 
     boolean isRemoved = names.remove(“Bob”);
     System.out.println(names);

     //Iterating over a HashSet
     for(String name: names){
      System.out.println(name);
      }
  }
} 

```

Output:

[Maria, Karen, Mike, Bob]

[Karen, Maria, Mike]

[Mike, Karen, Maria]

## LinkedHashSet

`LinkedHashSet` class is an ordered version of `HashSet`. It is the implementation of `LinkedList` in the `Set` Interface. Internally it uses a hash table with linked lists running through it to store the elements. It keeps the insertion order.
Example:

```java

import java.util.LinkedHashSet;
import java.util.Set;

public class LinkedHashSetExample{
  public static void main(String [] args){
     
     //Creating a HashSet
     Set <String> names = new LinkedHashSet<String>();

     //Adding new elements to the HashSet
     names.add(“Mike”);  
     names.add(“Bob”);
     names.add(“Maria”);
     names.add(“Karen”);
     names.add(“Mike”);

     System.out.println(names);

     //Removing an element of the HashSet 
     boolean isRemoved = names.remove(“Bob”);
     System.out.println(names);

     //Iterating over a HashSet
     for(String name: names){
      System.out.println(name);
      }
  }
} 

```
Output:

[Mike, Bob, Maria, Karen]

[Mike, Maria, Karen]

[Mike, Maria, Karen]

## TreeSet

`TreeSet` class implements the `Navigable` Interface which implements the
 `SortedSet` Interface. `SortedSet` gives functionalities to keep the elements sorted and `Navigable` gives functionalities to navigate through the `TreeSet`. Internally it uses a `TreeMap` to store the elements.TreeSet stores the elements by their natural order(alphabetical or numerical) or based on a custom `Comparator` that is supplied at the time a `TreeSet` is created.. You can not have  `duplicates` and `null` values in `TreeSet`. It is very useful for storing large amounts of sorted data because it accesses  and can retrieve data very fast.
Example:

```java

import java.util.SortedSet;
import java.util.TreeSet;

public class TreeSetExample{

  public static void main(String [] args){

     //Creating a TreeSet
     SortedSet<String> fruits = new TreeSet<String>();

     //Adding elements to a TreeSet
     fruits.add(“Peach”);
     fruits.add(“Apple”);
     fruits.add(“Pear”);
     fruits.add(“Banana”);

     System.out.println(fruits);
     
     //This will add element because it is lower case
     fruits.add(“apple”);
     System.out.println(fruits);
     
   }

}

```
Output:

[Apple, Banana, Peach, Pear]

[Apple, Banana, Peach, Pear, apple]

### TreeSet with a custom  comparator:

```java
import java.util.SortedSet;
import java.util.TreeSet;

public class TreeSetExample{

  public static void main(String [] args){

  //Creating a TreeSet using a Comparator
   SortedSet<String> fruits = new TreeSet<String>(String.CASE_INSESITIVE_ORDER);

     //Adding elements to a TreeSet
     fruits.add(“Peach”);
     fruits.add(“Apple”);
     fruits.add(“Pear”);
     fruits.add(“Banana”); 

     //Lower case will be duplicates now
     fruits.add(“apple”);

     System.out.println(fruits); 
  }
}
```
Output:

[Apple, Banana, Peach, Pear]





