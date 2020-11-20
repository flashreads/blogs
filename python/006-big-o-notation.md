---
id: 006-big-o-notation.md
title: What is Big O notation?
tags:
  - python
  - exceptions
author: Zoran Pandovski
meta-description: A beginners guide to the Big O notation
date: 2020-06-01 23:22:01 +0200
keywords: python, exceptions
template: post
categories:
  - python
cover: ../../images/categories/python.png
---

Let's preview the following simple fucntion:

```python
def sum(n):
    # note that := is assignment operator avaiable in Python 3.8
    sum = 0
    [sum := sum + x for x in n]
    return sum
```

Can you count the steps that are needed before returning the sum? Assigning the 0 value to sum, iterate over each `n` element and add it to the sum and lastly return the sum. Is there some mathematical notation that can describe this? Yes, that is the Big O notation. You can simply describe the efficiency of the algorithm with Big O notation. The Big O notation is used to describe the complexity of an algorithm according to the run time and space requirements when the different input size is used. Let me show you how it might look with code. 

```python
def find_awesome_user(users):
    for user in users:
        if user.city == 'awesome city':
            return user
    return 'Not found'
```

Before we found the user from an `awesome city` some number of checks must be performed. The user that we are looking can be the last in the list so we need to iterate through all of them which would be the worst-case scenario. Finding the user from the `awesome city` on the first iteration would be our best-case scenario. If we have the 50 users our average case scenario would fall somewhere in the middle, around 25 users. So, by analyzing the time complexity of the above function you can think of the best, average and worst-case scenarios. Big O notation measures the worst-case scenario. You can describe the complexity of this function as a linear because of the steps required to complete the execution of the function increase or decrease linearly with the number of users. You can say that the efficiency of the function is about O(n). 

Sometimes, an algorithm needs to perform a linear time operation for each value in the input data for e.g

```python
for x in data:
    for y in data:
        print(x, y)
```
In this case, it is a quadratic time complexity O(n2).

But what if the function doesn't depend on the input data? In that case, we can say that it has a constant time O(1).

```python
def find_first(users):
    #imagine the users were sorted by id
    return users[0]
```
This function doesn't depend on the input data size, because it always gets the first user from the list. 

By looking at the above examples maybe you can think of a use case where some algorithm has multiple complexities e.g O(n) + O(n2) + O(n!) etc. So, how can you calculate them, is just by describing the largest complexity of that algorithm. In the above example as O(n!) which is a factorial time complexity that grows in a factorial way.

![Big O Complexity chart](https://lukasmestan.com/assets/images/big-o-all.png)

For additional information on the Big O complexity of most common algorithms in the computer science check [bigocheatsheet](https://www.bigocheatsheet.com/).
