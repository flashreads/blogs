---
id: 001-string-equals-vs-equality-operator.md
title: Java String.equals vs '=='
tags: java, equals, comparison
author: Pavle Jonoski
meta-description: Learn how to properly compare string values in Java.
---

# Java String equals vs the (==) equality operator

> *TL;DR;* Always use `String.equals` or `Objects.equals` on strings. `==` compares
> memory locations, not the actual content of the string. This is important as
> string literals are not kept in the heap and different string objects on the
> heap will have different memory locations even if they have the same content.

Java is a bit weird when it comes to string comparison. I remember me getting
stumped when I first needed to compare strings in Java. I used the `==` comparison
operator and got some weird results that I didn't expect, for example:

```java
if("foo" == "foo") {
    // This always gets through
}

// However this
if(myVariable == "foo") {
    // would sometimes works, but other times will not work.
}
```

So what is going on?

It all stems from the way Java handles variables and constants in your code. 
Maybe you've heard of [string literals](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html "I thought of referencing the language specification for string literals, but that is just more confusing"). Literals in Java are primitive data types (like `int`,
`float`, `boolean` and sometimes `String`) which are not instantiated using the `new` keyword, like these
`int i = 10;` or `String str = "foo";`. Notice that there is no `new` keyword before any of these.

When defined like this, Java considers these values as constants and keeps them
in a special place in the jvm memory used for constants. The idea behind this is
a form of optimization - whenever Java encounters the same value in the code, it does
not allocate new memory on the heap, but instead will reuse the value that already
has in the static memory.

However, if we create new values using the `new` keyword, we're instructing the
jvm to actually allocate new slot on the heap for our value: `String str = new String("foo");`.
By now you may have some idea of what is going on:

```java
String a = "foo";  // this is a literal and goes in the static memory
String b = "foo";  // also a literal, with same value as 'a', so 'b' points to the same
                   // memory location as 'a'

String c = new String("foo")  // We allocate "foo" on the heap, although it has the
                              // same value as 'a' and 'b', it is in a different
                              // memory location - namely on the heap
```

When doing `==` comparison in Java, by default the jvm compares *memory locations* - it will
compare whether the memory address of the two objects is the same, and if it is, then the
objects must be the same.

But the strings allocated with `new` will always get new locations on the Heap, and `==`
will get two different memory locations and will evaluate to `false`.

The way around this is to use [`String.equals`](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#equals(java.lang.Object)) method.
This method compares the string content, and *not* the memory addresses. And that is what we want
when comparing strings.

Here is some weirdness and examples on how to compare string and what not to do:

```java

String a = "foo";
String b = "foo"; 

a == b  // -> true, but don't do this.

a.equals(b)  // true. Do this instead.

String a = "foo";
String b = new String("foo")

a == b  // false. One is a string literal, the other is a regular object on the heap.

a.equals(b) // true. Compares the content: "foo" is equal to "foo".


// Alternative approach, with Objects.equals
Objects.equals("foo", "foo")               // true
Objects.equals("foo", null)                // true. Protects us from null pointer dereferencing.
Objects.equals("foo", new String("foo"))   // true

```

So basically we want to use `String.equals` to compare the content of the strings. However
in some cases we may run into problems, namely in the cases when we try to call `equals` from
a variable that is `null`:

```java
String a = null;

a.equals("foo");  // NullPointerException

```

So in cases when we're comparing with a literal, always call equals from the literal:

```java
String a = null;

"foo".equals(a)   // false. No exception was thrown.
```

Alternatively you can use [`Objects.equals`](https://docs.oracle.com/javase/8/docs/api/java/util/Objects.html#equals-java.lang.Object-java.lang.Object-) (available from java 1.7).
This does what we want and takes care of the `null` values.

```java
String a = null;

Objects.equals(a, "foo") // false. no exception thrown.
```