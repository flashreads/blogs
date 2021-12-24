---
id: 015-data-encapsulation-in-java.md
title: Data Encapsulation In Java
tags:
  - encapsulation
  - OOP
  - Class
author: Vasav Prashar
meta-description: Learn about Abstract Classes in Java
date: 2021-10-05 10:37:31 +0600
keywords: encapsulation, OOP, Class
template: post
categories:
  - java
image: assets/images/java/data.svg
---

# ENCAPSULATION

`Encapsulation` is defined as the wrapping up of data under a single unit. It is the mechanism that binds together code and the data it manipulates.
In `Encapsulation`, the variables or data of a class is hidden from any other class and can be accessed only through any member function of its own class in which it is declared.

It is also known as a `combination of data-hiding and abstraction.`

## Implementation of DATA ENCAPSULATION in JAVA

Program to show Data Enacpsulation:

```java
class Encapsulate {
    // private variables declared
    // these can only be accessed by
    // public methods of class
    private String StudentName;
    private int StudentRoll;
    private int StudentAge;
 
    // get method for age to access
    // private variable StudentAge
    public int getAge() { return StudentAge; }
 
    // get method for name to access
    // private variable STudentName
    public String getName() { return StudentName; }
 
    // get method for roll to access
    // private variable StudentRoll
    public int getRoll() { return StudentRoll; }
 
    // set method for age to access
    // private variable Studentage
    public void setAge(int newAge) { StudentAge = newAge; }
 
    // set method for name to access
    // private variable StudentName
    public void setName(String newName)
    {
        StudentName = newName;
    }
 
    // set method for roll to access
    // private variable StudentRoll
    public void setRoll(int newRoll) { StudentRoll = newRoll; }
}
 
public class TestEncapsulation {
    public static void main(String[] args)
    {
        Encapsulate obj = new Encapsulate();
 
        // setting values
        obj.setName("Vasav");
        obj.setAge(19);
        obj.setRoll(51);
 
        System.out.println("Student name: " + obj.getName());
        System.out.println("Student age: " + obj.getAge());
        System.out.println("Student roll: " + obj.getRoll());
 
        // Direct access of StudentRoll is not possible
        // due to encapsulation
    }
}

```
Output
```
Student name: Vasav
Student age: 19
Student roll: 51
```

In the above program, the class Encapsulate is encapsulated as the variables are declared as private. The `get` methods like getAge() , getName() , getRoll() are set as public, these methods are used to access these variables. The `setter` methods like setName(), setAge(), setRoll() are also declared as public and are used to set the values of the variables.

## Uses And Advantages Of Data Abstraction

1. `Data Hiding`: The user will have no information about the private data variables.
2. `Increased Flexibility`
3. Use in Big e-Commerce websites.
4. It reduces Human error.