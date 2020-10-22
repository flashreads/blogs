---
id: 007-java-collections-hierarchy.md
title: Java Collection Hierarchy
tags: java, collection, API, List, Set, Queue
author: Kosta Lazarevski
meta-description: Learn about Java Collection Framework hierarchy
---

# Java Collection Hierarchy

Java Collection Framework was introduced in Java 1.2 version. Collections are containers that group multiple items in a single unit. Collection is an object that represents a group of objects. Collections are dynamic containers that allow you to add or remove items at runtime. It provides an architecture to store and manipulate groups of objects. It allows  you to search, sort and manipulate data. It provides interfaces and classes in order to store the data in different data structures.

Java Collections hierarchy is a set of API`s,  linked between them in parent - child relation.  This is a diagram that shows the hierarchy from the root interface: The Collection Interface(java.util.Collection).

![Java collection diagram](https://static.javatpoint.com/images/java-collection-hierarchy.png)

From the diagram of the Collection interface we can see three main data structures in List, Queue and Set. All of these data structures are manipulating only with values(the iterator uses index to check or add or retrieve  element).The methods that contain the algorithms that perform the computations(sorting, searching, etc…) are polymorphic. One method can be used on many implementations of the right collection Interface. Methods(algorithms) are reusable.This means that we get to work with super arrays.
