---
id: 021-type-comparison
title: Type Comparison
tags: java, object, type
date: 2021-10-28 21:53:39 +0200 
keywords: java, object, type
categories: java
cover: ../../images/categories/java.png
author: Alla Konstantinova
meta-description: Type Comparison in Java
---

# Type Comparison

The most common way to determine if a given object is an **instance** of a given class, superclass or interface, is by using the binary operator `instanceof`. It includes implicit null check and generates a compile-time error if the types are not related. But it doesn't allow primitives and requires the types to be know at compile time. 

## If you want to check dynamically at runtime
Use the equivalent method `boolean isInstance(Object obj)` in `Class`. It also includes null check, but allows for primitives:

```java
    a instanceof B 
    // returns false for null
    null instanceof B

    a.getClass().isInstance(b);
    // commonly used for generics
    Class<T> type = b.getClass();
    type.isInstance(a);

    // Note that the parameter is autoboxed to type Integer
    int x = 4;
    Integer.class.isInstance(x);
```

## Check compatibility of two types
When you need to check subtyping relation use the method `boolean isAssignableFrom(Class<?> cls)` in `Class`. It may throw _NullPointerException_.

```java
    // is it possible to B b = new A()
    Class<?> aClass = CharSequence.class;
    Class<?> bClass = String.class;
    bClass.isAssignableFrom(aClass());

    // works for arrays
    CharSequence[].class.isAssignableFrom(String[].class); // true
    Integer[].class.isAssignableFrom(String[].class); //false
```

## Pattern Matching (Java 14)
```java
    if(a instanceof B b) {
        // b is casted
        b.toString();
    }
```

## Special types
```java
    // Enums
    enum Color { WHITE, GRAY, BLACK }

    Color.class.isEnum(); // Enum.class.isAssignableFrom(Color.class); 
    Color.WHITE instanceof Enum; // true

    // Arrays
    String[].class.isArray();
    // get the type of the variables in an array (null if obj is not an array)
    Class<?> componentType = obj.getComponentType(); 

    // Primitives
    int.class.isPrimitive();
```
