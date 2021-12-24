---
id: 013-abstract-classes-in-java.md
title: Abstract Classes in Java
tags:
  - abstraction
  - OOP
  - Class
author: Kosta Lazarevski
meta-description: Learn about Abstract Classes in Java
date: 2020-11-04 19:58:39 +0100
keywords: abstraction, OOP, Class
template: post
categories:
  - java
image: assets/images/java/abstract.svg
---

# Abstraction

Abstraction is a process of hiding the implementation details and showing only functionality to the user. Focus is set on the purpose of the object and not it's functionality.

## CLasses

A class which is declared with the `abstract` keyword is an abstract class in Java. It can have Abstract methods(no body) and Non-abstract methods(has a body). An abstract class can not be initiated, meaning we can`t create an onject of its type.

Let's see why do we need abstract classes.

Let's say that we hava a class Aimal that has a lot of subclasses(Dog, Cat, etc.) We don`t want to hava an Animal object becouse we only model a certain animals.
Here is an example:

```java
abstract class Animal{
  //abstract methods
  public abstract void sound(); //no body
  }
public class Dog extends Animal{

  @Override //impleenting the abstract method
  public void sound(){
  System.out.println("Woof!")
  }

public static void main(String args[]) {
  Animal obj = new Dog();
  obj.sound();
  }

}
```

## When to use abstract classes

1. An abstract class is a good choice if we are using the inheritance concept since it provides a common base class implementation to derived classes.
2. An abstract class is good to use if we want to declare non-public members. In an interface, all methods must be public.
3. If we want to add new methods in the future, then an abstract class is a better choice. Because if we add new methods to an interface, then all of the classes that already implemented that interface will have to be changed to implement the new methods.
4. If we want to create multiple versions of our component, create an abstract class. Abstract classes provide a simple and easy way to version our components. By updating the base class, all inheriting classes are automatically updated with the change. Interfaces, on the other hand, cannot be changed once created. If a new version of an interface is required, we must create a whole new interface.
5. If we want to provide common, implemented functionality among all implementations of our component, use an abstract class. Abstract classes allow us to partially implement our class, whereas interfaces contain no implementation for any members.
