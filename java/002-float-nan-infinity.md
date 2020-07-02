---
id: 002-float-nan-infinity.md
title: NaN and Infinity in Java
tags: java, nan, infinity, positive-infinity, negative-infinity
author: Pavle Jonoski
meta-description: NaN, Positive Infinity and Negative Infinity in Java
---

# NaN and Infinity in Java

You maybe familiar with the fact that you cannot divide an integer with 0 in Java - it yields `java.lang.ArithmeticException: / by zero`.
But what happens when we try to do this with floating point numbers.

Let's give it a try:

```java
int m = 10, n = 0;

System.out.println(m/n);
// Exception: java.lang.ArithmeticException: / by zero

float a = 10.0f, b = 0.0f;
System.out.println(a/b);
// Infinity

```

Now that is interesting, we didn't get an exception, but instead we got something as a result: `Infinity`.

If we check out the `Float` class, we can see that there are a couple of constants defined in the class:

* `NaN` - A constant holding a Not-a-Number (NaN) value of type float.
* `PositiveInfinity` - A constant holding the positive infinity of type float.
* `NegativeInfinity` - A constant holding the negative infinity of type float.

What this means is, that some operations in Java may yield values that are not strictly some defined number and behave in a special way.
For example, when we're diving by `0`, we usually say that the result is Infinity. In maths this has a special meaning, in terms that
Infinity is not a specific number and has a set of rules defined for it. In Java we can see that there are two types of infinity: positive and negative.

To get a positive infinity, it means that the result of some operation approaches infinite value, but from the positive side on the number axis - for
example if we divide a positive number by 0, we get infinite results but all of them are positive, thus getting positive infinity.
On the other hand if we divide a negative number by 0, we also get infinite results, but all of them are negative, so negative infinity.

```java
float a = 1.0f;
float b = 0.0f;

System.out.println((a/b) == Float.POSITIVE_INFINITY);
// true

// if a is negative
a = -1.0f;
System.out.println((a/b) == Float.POSITIVE_INFINITY);
// false, we should be getting negative infinity

System.out.println((a/b) == Float.NEGATIVE_INFINITY);
// true

```


But what happens when both of the numbers are `0`? In maths, dividing zero by zero yields an undefined result.

In Java we get `NaN`. This is also a constant defined in `Float` and `Double` classes.
If we try to divide zero by zero, we get something that is not a number, so `NaN`.

```java
float a = 0.0f;
float b = 0.0f;
Float c = a/b;

System.out.println(c);
// NaN
System.out.println(c == Float.NaN);
// false
System.out.println(c.isNaN());
// true
```

Now this looks weird. Why isn't the result (`c`), which is clearly `NaN`, not equal to that constant?

This also comes from maths, where we cannot compare two things that are not numbers. We can only compare something that has 
a clear definition or has a clear value. NaN denotes a mathematically undefined value, and as such we cannot compare it (similar to `NULL` in `SQL`).

What we *can* do, is to check whether whatever we got is undefined (Not-a-Number) by using `Float.isNaN()` method.

## Some notes on serialization

When serializing special care should be taken to serialize these values properly.
If we do naive serialization, we would get an exception:

```java
Gson gson = new Gson();
System.out.println(gson.toJson(new SomeObject(10.0f/0.0f)));
// Throws an exception: java.lang.IllegalArgumentException: Infinity is not a valid double value as per JSON specification. To override this behavior, use GsonBuilder.serializeSpecialFloatingPointValues() method.
```

By setting the serialization of these values, we get the following:

```java
public static class SomeObject {
    private float value;

    public SomeObject(float value) {
        this.value = value;
    }

    public float getValue() {
        return value;
    }

    public void setValue(float value) {
        this.value = value;
    }
}

...

GsonBuilder builder = new GsonBuilder();
builder.serializeSpecialFloatingPointValues();
Gson gson = builder.create();

System.out.println(gson.toJson(new SomeObject(10.0f/0.0f)));
// {"value":Infinity}

System.out.println(gson.toJson(new SomeObject(-10.0f/0.0f)));
// {"value":-Infinity}

System.out.println(gson.toJson(new SomeObject(0.0f/0.0f)));
// {"value":NaN}
```

Be careful though, these values may not be recognized by some JSON parsers and you may get some unpredictable results, such as
the values to be converted to `String` or getting an error while parsing.
