---
id: 012-map-interface-in-java.md
title: Map Interface in Java
tags:
  - java
  - collection
  - API
  - Map
  - HashMap
  - LinkedHashMap
  - TreeMap
author: Kosta Lazarevski
meta-description: Learn how to use Map interface to store, manipulate data in Java
date: 2020-11-01 14:33:33 +0100
keywords: java, collection, API, Map, HashMap, LinkedHashMap, TreeMap
template: post
categories:
  - java
cover: ../../images/categories/java.png
---

# Map Interface

A `Map` contains values on the basis of key, i.e. key and value pair. Each key and value pair is known as an entry. A Map contains unique keys.
A Map is useful if you have to search, update or delete elements on the basis of a key.

A Map is an object that maps keys to values. A map cannot contain duplicate keys: Each key can map to at most one value. The Map interface includes methods for basic operations (such as `put()`, `get()`, `remove()`, `containsKey()`, `containsValue()`, `size()`, and `empty()`), bulk operations (such as `putAll()` and `clear()`), and collection views (such as `keySet()`, `entrySet()`, and `values()`). A Map is useful if you have to search, update or delete elements on the basis of a key.

The Java platform contains three general-purpose `Map` implementations: `HashMap`, `TreeMap`, and `LinkedHashMap`. Their behavior and performance are precisely analogous to `HashSet`, `TreeSet`, and `LinkedHashSet`.

This is Map Interface('java.util.Map') hierarchy:

![Java Map hierarchy](https://static.javatpoint.com/images/core/java-map-hierarchy.png)

## HaspMap

HashMap is the implementation of Map, but it doesn't maintain any order.
Lets an examples of HashMap implementation:

```java

// Import the HashMap class
import java.util.HashMap;

public class MyClass {
  public static void main(String[] args) {
    // Create a HashMap object called capitalCities
    HashMap<String, String> capitalCities = new HashMap<String, String>();

    // Add keys and values (Country, City)
    capitalCities.put("England", "London");
    capitalCities.put("Germany", "Berlin");
    capitalCities.put("Norway", "Oslo");
    capitalCities.put("USA", "Washington DC");
    System.out.println(capitalCities);
  }
}
```

 Output: 
 
{USA=Washington DC, Norway=Oslo, England=London, Germany=Berlin}

## LinkedHasMap

Java `LinkedHashMap` class is `Hashtable` and `LinkedList` implementation of the `Map` interface, with predictable iteration order. It inherits `HashMap` class and implements the `Map` interface.

```java
import java.util.LinkedHashMap;
import java.util.Set;
import java.util.Iterator;
import java.util.Map;
public class LinkedHashMapDemo {
    public static void main(String args[]) {
         // HashMap Declaration
         LinkedHashMap<Integer, String> lhmap = 
                 new LinkedHashMap<Integer, String>();

         //Adding elements to LinkedHashMap
         lhmap.put(22, "Abey");
         lhmap.put(33, "Dawn");
         lhmap.put(1, "Sherry");
         lhmap.put(2, "Karon");
         lhmap.put(100, "Jim");

         // Generating a Set of entries
         Set set = lhmap.entrySet();

         // Displaying elements of LinkedHashMap
         Iterator iterator = set.iterator();
         while(iterator.hasNext()) {
            Map.Entry me = (Map.Entry)iterator.next();
            System.out.print("Key is: "+ me.getKey() + 
                    "& Value is: "+me.getValue()+"\n");
         }
    }
}
```
Output:

Key is: 22& Value is: Abey

Key is: 33& Value is: Dawn

Key is: 1& Value is: Sherry

Key is: 2& Value is: Karon

Key is: 100& Value is: Jim

## TreeMap

The `TreeMap` in Java is used to implement `Map` interface and `NavigableMap` along with the `AbstractMap` Class. The map is sorted according to the natural ordering of its keys, or by a `Comparator` provided at map creation time, depending on which constructor is used.

```java
import java.util.TreeMap;
import java.util.Set;
import java.util.Iterator;
import java.util.Map;

public class Details {

   public static void main(String args[]) {

      /* This is how to declare TreeMap */
      TreeMap<Integer, String> tmap = 
             new TreeMap<Integer, String>();

      /*Adding elements to TreeMap*/
      tmap.put(1, "Data1");
      tmap.put(23, "Data2");
      tmap.put(70, "Data3");
      tmap.put(4, "Data4");
      tmap.put(2, "Data5");

      /* Display content using Iterator*/
      Set set = tmap.entrySet();
      Iterator iterator = set.iterator();
      while(iterator.hasNext()) {
         Map.Entry mentry = (Map.Entry)iterator.next();
         System.out.print("key is: "+ mentry.getKey() + " & Value is: ");
         System.out.println(mentry.getValue());
      }

   }
}
```

Output:

key is: 1 & Value is: Data1

key is: 2 & Value is: Data5

key is: 4 & Value is: Data4

key is: 23 & Value is: Data2

key is: 70 & Value is: Data3
