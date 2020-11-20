---
id: 024-ProjectEulerProblem1.md
title: Solving Project Euler's Problem 1 with Python
tags:
  - Python
  - Project Euler
  - Algortithms
author: Felix Ayoola
meta-description: Learn the about solving project Euler's Problem 1 in Python.
date: 2020-10-30 19:41:07 +0100
keywords: Python, Project Euler, Algortithms
template: post
categories:
  - python
cover: ../../images/categories/python.png
---

# Project Euler

let us first learn what the Project Euler is:

Project Euler is a website dedicated to a series of computational problems intended to be solved with computer programs. The project attracts adults and students interested in mathematics and computer programming. Since its creation in 2001 by Colin Hughes, Project Euler has gained notability and popularity worldwide.


## why Python?
I find Python to be very simple and its syntax is very close to english.


## What is the problem?
if we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Find the sum of all the multiples of 3 or 5 below 1000.

## How do we approach this problem?
1.  The first step in solving any problem, is to understand the problem first, make sure you can communicate the problem to someone else in your own way without losing the focus. 


2.  Write down the problem in pseudocode, this is more like english, so for example you might start this problem's pseudocode like this

    1. Pick all numbers that falls below 1000,
    2. Check if the number is a multiple of 3 or 5,
    3. Add all numbers that fulfil (2) and print the sum.


## Create an algorithm to implement in your code
This would be a step by step process on how you intend to write the code that solves the problem.

Let us write and algorithm for our problem:

1.  initiate a variable 'count' that will hold the sum of the numbers.
2.  Use the range function to go through all numbers below 1000(Exclusive)
3.  Check if the number is a multiple of 3 using the '%' operator and increment the variable 'count' if this condition is true.
4.  Check if the number is a multiple of 5 using the '%' operator and increment the variable 'count' if this condition is true.
5.  print the count variable which by now contains the sum of all multiples of 3 or 5 out.

## Note
I don't always go through this process religiously, so don't worry yourself, look at the problem and do whatever works for you. Just make sure you solve the problem.

```python
#initiate the count variable
count = 0
#Use the range function to go through all numbers below 1000(Exclusive)
for i in range(1,1000):
    #Check if the number is a multiple of 3 using the '%' operator
    if i%3==0:
        count += i
    #Check if the number is a multiple of 5 using the '%' operator
    elif i%5==0:
        count += i
#print the count variable which by now contains the sum of all multiples of 3 or 5 out
print (count)
```

## Conclusion:
So this was a 1-minute read article on using Python to solve Project Euler's Problem 1. There is no one way to solve this problem, you can choose to use list comprehension and list.sum method, it depends on you.  I hope this article helps you to get started with using python to solve problems, you can try the more difficult ones, I should be adding another article on another problem soon.

Thank you!! 