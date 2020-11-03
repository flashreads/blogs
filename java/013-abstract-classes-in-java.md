---
id: 013-abstract-classes-in-java.md
title: Abstract Classes in Java
tags: abstraction, OOP, Class
author: Kosta Lazarevski
meta-description: Learn about Abstract Classes in Java
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

