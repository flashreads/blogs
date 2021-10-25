---
id: 018-cryptographically-secure-random.md
title: Cryptographically Secure Random in Java
tags:
    - java
    - random
    - crypto
date: 2021-10-24 23:56:00 +0200 
keywords: random, java, cryptographically-secure
categories:
    - java
cover: ../../images/categories/java.png
author: Pavle Jonoski
meta-description: generate cryptographically secure random number in Java
---

# Generate cryptographically secure random number in Java

In many cases you might need to generate a cryptographically secure random number. The difference between a random number
generated using the standard [Random](https://docs.oracle.com/javase/8/docs/api/java/util/Random.html) generator or via [ThreadLocalRandom](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/ThreadLocalRandom.html), is that the algorithm used to generate the
pseudo-random number ([PRNG](https://en.wikipedia.org/wiki/Pseudorandom_number_generator)) is usually cryptographically strong i.e. the probability of predicting the random number is very
small. The typical usage of such generated numbers and values is when you need to generate a secret key/password or other random bytes which are hard to guess and most often used in authentication/authorization flows, or when generating random secret keys for encryption.

To generate a cryptographically secure random numbers or sequences in Java, you should use [`SecureRandom`](https://docs.oracle.com/javase/8/docs/api/java/security/SecureRandom.html).

Here is a simple example of generating a random integer:

```java
SecureRandom random = new SecureRandom();
var i = random.nextInt();
System.out.println("This is my random number: " + i);
```
`SecureRandom` extends the `Random` class and implements all methods already exposed in `Random`, so it can be used as a drop-in replacement for it.

Here are some more examples.

Generate a random sequence of bytes:

```java
SecureRandom random = new SecureRandom();

byte[] buffer = new byte[128];
random.nextBytes(buffer);
// we have now generated a 128 bytes with random values.
```

Generate a random [base64](https://en.wikipedia.org/wiki/Base64) string:

```java
import java.security.SecureRandom;
import java.util.Base64;

public class CryptoSafeRandom {

    public static void main(String[] args) {
        SecureRandom random = new SecureRandom();
        var buffer = new byte[12];
        random.nextBytes(buffer);
        String randomString = Base64.getEncoder().encodeToString(buffer);
        System.out.println("This is my cryptographically secure random string: " + randomString);
    }
}
```

Output:
```
This is my cryptographically secure random string: D++46PI36dOUmhHI
```