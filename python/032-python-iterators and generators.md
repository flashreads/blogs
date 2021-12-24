---
id: 032-python-iterators and generators.md
title: Iterators and Generators in Python
tags:
  - python
  - random
author: Hammed Babatunde
meta-description: Using iterators and Generators in Python
date: 2021-10-11 18:38:42 -0700
keywords: python
template: post
categories:
  - python
image: assets/images/python/python4.svg
---

# Generators and Iterators in Python 

Generator functions allow us to write a function that can send back a value and then later resume to pick up where it left off. This type of function is a generator in Python, allowing us to generate a sequence of values over time. The main difference in syntax will be the use of a yield statement.

In most aspects, a generator function will appear very similar to a normal function. The main difference is when a generator function is compiled they become an object that supports an iteration protocol. That means when they are called in your code they don't actually return a value and then exit. Instead, generator functions will automatically suspend and resume their execution and state around the last point of value generation

￼￼ To start getting a better understanding of generators, let's go ahead and see how we can create some.

```python
# Generator function for the cube of numbers (power of 3)
def gencubes(n):
    for num in range(n):
        yield num**3

for x in gencubes(10):
    print(x)
```
Generators are best for calculating large sets of results (particularly in calculations that involve loops themselves) in cases where we don’t want to allocate the memory for all of the results at the same time.

Let's create another example generator which calculates fibonacci numbers:
```python
# Generator function for the cube of numbers (power of 3)
def genfibon(n):
    """
    Generate a fibonnaci sequence up to n
    """
    a = 1
    b = 1
    for i in range(n):
        yield a
        a,b = b,a+b

for num in genfibon(10):
    print(num)
```

## next() built-in function in Python
A key to fully understanding generators is the next() function and the iter() function.

The next() function allows us to access the next element in a sequence. Lets check it out:
```python
# Generator function for the cube of numbers (power of 3)
def simple_gen():
    for x in range(3):
        yield x

# Assign simple_gen 
g = simple_gen()

print(next(g)) #prints out a value in the generator
```

## iter() built-in Fuction in Python
Let's go ahead and check out how to use iter()
 A string object supports iteration, We can directly iterate over a string with The iter() function.
```python
s = 'hello'

#Iterate over string
for let in s:
    print(let)

s_iter = iter(s)

next(s_iter) # print each of the value in s when called 
```

The main takeaway from this article is that using the yield keyword at a function will cause the function to become a generator. This change can save you a lot of memory for large use cases.
