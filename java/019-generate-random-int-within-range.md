---
id: 019-generate-random-int-within-range.md
title: Generate a random integer within specific range
tags:
    - java
    - random
    - integer
    - range
date: 2021-10-25 00:35:30 +0200 
keywords: generate, random, integer, range, java
categories:
    - java
cover: ../../images/categories/java.png
author: Pavle Jonoski
meta-description: learn howto generate a random integer within a specific range in Java
---

# Generate a random integer within specific range in Java

Very often you need to generate a random number within some range.
Java offers a [`Random.nextInt(int bound)`]() method, which gives you a random integer between `0` (inclusive) and the `bound` (exclusive).

We can use this method to generate a random number between `a` and `b`:

```java
public static int nextRandomIntBetween(int a, int b) {
    if (b <= a) {
        throw new IllegalArgumentException("b must be greater than a");
    }
    int m = b - a;
    Random random = new Random();
    return random.nextInt(m) + a;
}
```

First, we must ensure that `b` is greater than `a`. `nextInt(int bound)` does not accept negative values.
Then, we calculate the difference `b - a`. This is the range of our random integers and we can use this
to generate random number between 0 and `b - a`.
Finally, we add the value of `a` to the random number, which will make the random number exactly in the range
we wanted.

Here is the full example:

```java
package com.flashreads.examples;

import java.security.SecureRandom;
import java.util.Base64;
import java.util.Random;

public class RandomNumberWithinRangeExample {

    public static void main(String[] args) {
        System.out.println("Here are 10 numbers between 5 (inclusive) and 8 (exclusive):");
        for(int i = 0; i < 10; i++) {
            System.out.println(nextRandomIntBetween(5, 8));
        }

    }


    public static int nextRandomIntBetween(int a, int b) {
        if (b <= a) {
            throw new IllegalArgumentException("b must be greater than a");
        }
        int m = b - a;
        Random random = new Random();
        return random.nextInt(m) + a;
    }
}

```

Output:

```
Here are 10 numbers between 5 (inclusive) and 8 (exclusive):
6
7
5
5
5
6
7
7
6
6
```