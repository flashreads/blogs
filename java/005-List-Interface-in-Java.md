---
id: 005-list-interface-in-java.md
title: List interface in Java
tags: java, collection, list, array list, linked list,vector
author: Kosta Lazarevski
meta-description: Learn how to use List interface to store, manipulate data in Java
---

# List Interface

The List Interface `java.util.List` represents an ordered list of elements(objects). The elements in the list can be inserted, accessed, iterated and removed by their index (by order in which they  appear in the List). 
Each element has an index. The first element in the list has an index of 0, and the index increments  with adding of elements. The list can have duplicate elements. 
`ArrayList`, `LinkedList` and `Vector` are the three classes that implement the `List Interface`.


## ArrayList

`ArrayList` is the simplest and most often used member of Java Collections Framework. Contrary to Arrays that are fixed, ArrayList can increment and decrement its size when new elements are added or removed. It is a dynamic `Array`. It allows null values and duplicates. You can retrieve elements by their index that are ordered by their insertion.The ArrayList always manage arrays internally
Example: [0] [1] [2] [3] [4].... . 
You must use boxed types `Integer`, `Character`, etc when creating an `ArrayList` instead of primitives: int, char, etc….

Creating an ArrayList example:

```java
import java.util.ArrayList;
import java.util.List;    
public class ArrayListExample{

 Public static void main(String [] args){
     
    // Creating an ArrayList of Strings
     List<String> pets = new ArrayList<String>();




   // Adding elements to the list

    pets.add("dog");
    pets.add("cat");
    pets.add("fish");

    System.out.println(pets);

    pets.add(1, “turtle”);

    System.out.println(pets);

    //Retrieve element at a given index
    String myPet = pets.get(0);
     
    System.out.println(“My pet is a ” + myPet + “.”);

    //Remove element at a given index
     pets.remove(3);
     
     System.out.println(pets);

    //Iterating over an ArrayList
     for(String allPets : pets){
       System.out.println(allPets)
     }

   }
}
```

Output:

[dog, cat, fish]

[dog, turtle, cat, fish]

My pet is a dog.

[dog, turtle, cat]

[dog, turtle, cat]

These are the basic and most used methods for adding, removing and retrieving elements in an ArrayList. You can check if the List is empty with isEmpty(); method, the size of the list size(); remove an object remove (Object obj); Get the first or last element getFirst(); getLast(); Check if the list contains some element contains(); and many more methods.


## LinkedList

`LinkedList` implements the List interface same as the `ArrayList` and they are very similar to use. The difference between them is the way they store the elements and the way they link to the elements. LinkedList stores the elements in a double links list. Every element is pointing to the next and the previous element. 
Example: [0] => [1] =>  [2] =>  [3] => [4]
                [0] <= [1] <=  [2] <=  [3] <= [4]
`LinkedList` has a better performance  on `add()` and `remove()` than `ArrayList` because there is no shifting of the elements but is slower on `get()` and `set()` methods. LinkedList maintains insertion order, and can have `null` and duplicate values. LinkedList Implements the List Interface, but also implements the `Queue Interface`, that adds additional methods such as `offer()`, `poll()`, `peek()`,
 
Creating a LinkedList example:

```java
import java.util.LinkedList;
import java.util.ArrayList;
import java.util.List;    
public class LinkedListExample{

 Public static void main(String [] args){
     
    // Creating a LinkedList of Strings
     List<String> pets = new LinkedList<String>();




   // Adding elements to the list 

    pets.add("dog");
    pets.add("cat");
    pets.add("fish");

    System.out.println(pets);

    pets.add(1, “turtle”);

    System.out.println(pets);

    //Retrieve element at a given index
    String myPet = pets.get(0);
     
    System.out.println(“My pet is a ” + myPet + “.”);

    //Remove element at a given index
     pets.remove(3);
     
     System.out.println(pets);

    //Iterating over an LinkedList 
     for(String allPets : pets){
       System.out.println(allPets)
     }
   }
}

```

Output:

[dog, cat, fish]

[dog, turtle, cat, fish]

My pet is a dog.

[dog, turtle, cat]

[dog, turtle, cat]

## Vector


`Vector` is almost identical to an `ArrayList`, they are similar to use.  The difference is that ArrayList is not synchronized and the Vector is synchronized. The ArrayList increases its capacity by 50% and Vector increases its capacity by 100% if their number of elements exceeds its capacity. Vector is slow because it is synchronized. ArrayList is more commonly used over Vector because you can synchronize it by yourelves.

```java
mport java.util.*;

public class VectorExample {

   public static void main(String args[]) {
      /* Vector of initial capacity(size) of 2 */
      Vector<String> vec = new Vector<String>(2);

      /* Adding elements to a vector*/
      vec.addElement("Apple");
      vec.addElement("Orange");
      vec.addElement("Mango");
      vec.addElement("Fig");

      /* check size and capacityIncrement*/
      System.out.println("Size is: "+vec.size());
      System.out.println("Default capacity increment is: "+vec.capacity());

      vec.addElement("fruit1");
      vec.addElement("fruit2");
      vec.addElement("fruit3");

      /*size and capacityIncrement after two insertions*/
      System.out.println("Size after addition: "+vec.size());
      System.out.println("Capacity after increment is: "+vec.capacity());

      /*Display Vector elements*/
      Enumeration en = vec.elements();
      System.out.println("\nElements are:");
      while(en.hasMoreElements())
         System.out.print(en.nextElement() + " ");
   }
}
```
Output:

Size is: 4

Default capacity increment is: 4

Size after addition: 7

Capacity after increment is: 8


Elements are:

Apple Orange Mango Fig fruit1 fruit2 fruit3








