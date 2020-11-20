---
id: 008-java-interface-changes-java-8
title: Changes behavior interface - Java 8
tags:
  - java
  - interface
  - default method
  - static static
author: Lucas Freire
meta-description: change behavior interface in Java 8
date: 2020-10-25 18:56:27 -0300
keywords: java, interface, default method, static static
template: post
categories:
  - java
cover: ../../images/categories/java.png
---

# What is interface in Java

Another way to achieve abstraction In Java. An interface is like a "abstract class" that used is used to group related methods. However, an interface have some features that distinct an abstract class:
- An concrete class can implement one or more interfaces
- An interface can extend one or more interfaces

```

public class Test implements Interface1,Interface2,Interface3 {
    //methods...
}

public interface Interface extends Comparator<T>, Runnable {

}


```

If you try extends interface in concrete class, you will have a java compiler error. The same will pass, whether try implements interface using another interface.
These examples will be compiler error:

```

public interface Test implements Interface1,Interface2,Interface3 {
    //methods...
}

public class Interface extends Comparator<T>, Runnable {

}


```

# What change

With Java 8, the interface can have concrete methods and static methods. Before this version, the interface could not have concrete methods or static methods. 

For create a concrate method in interface, the method must be the keyword **default** in the signature. Example:

```

public default void test(){
 //code
}

public static void staticMethod(){
 //code
}

```

With this, it is possible add to interface some methods without broken classes that implement it(maintaining compatibility).
For example, before java 8 the interface List does not have the method "sort". 

If the java programmers wanted to add behavior in the java.util.List without change your subtypes (Vector, ArrayList and others), will be not possible. If they add the behavior, your subtypes will be obligated to change your code to compile and maintain compability. 

To make the behavior transparent to your subtypes, now they can use the default method to add some features without obligated your subtypes change code.


## Inherits Behavior

Imagine you have two interfaces with the same default method. What happens with subtype implements the two interfaces?
The subtype will be obligated override the method. If no, will have a compiler error.

```
public interface Test1 {

	public default void test() {
		System.out.println("Test 1 method");
	}

}

public interface Test2 {

	public default void test() {
		System.out.println("Test 2 method");
	}

}

public class Test implements Test1, Test2 {
// Java compiler error

}

```

If the interface have static methods, you must use the interfacename.staticmethodname.
When we extend the class with static method, you can use the subclass to call the static method. However, if the interface it is not possible.

```

public class Parentclass {

	public static void testeMethodParent() {

	}

}

public interface Test1 {

	public default void test() {
		System.out.println("Test 1 method");
	}

	public static void teste() {

	}

}

public class Test extends Parentclass implements Test1 {

	public static void main(String[] args) {
		Test.testeMethodParent(); // OK
		Test1.testeStaticMethodInterface(); // OK
		Test.testeStaticMethodInterface(); // ERROR
	}

}

```