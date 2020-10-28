---
id: 017-NumPy.md
title: Python NumPy Array
tags: Python, NumpPy, array
author: Daita Sur
meta-description: Learn the about NumPy array in Python.
---

# NumPy in Python

let us first learn what is NumPy:

NumPy is a python library used for working with arrays. It also has functions for working in the domain of linear algebra, Fourier transform, and matrices. NumPy is an open-source project and we can use it freely. NumPy stands for Numerical Python.


## why should we use NumPy?
In Python, we have lists that serve the purpose of arrays, but they are slow to process. NumPy aims to provide an array object that is up to 50 times faster than traditional Python lists. The array object in NumPy is called ndarray. It provides a lot of supporting functions that make working with ndarray very easy.


## Where is NumPy used?
Python NumPy arrays provide tools for integrating C, C++, etc. It is also useful in linear algebra, random number capability, etc. NumPy array can also be used as an efficient multi-dimensional container for generic data. 

## Why is NumPy Faster than lists?
NumPy arrays are stored at one continuous place in memory unlike lists, so processes can access and manipulate them very efficiently.

now let us learn how to create an array using NumPy:

## Create a NumPy ndarray Object
NumPy is used to work with arrays. The array object in NumPy is called ndarray.
We can create a NumPy ndarray object by using the array() function.
```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])

print(arr)

print(type(arr))

```
OUTPUT:
[1 2 3 4 5]
<class 'numpy.ndarray'>

## Joining NumPy Arrays

Joining means putting contents of two or more arrays in a single array.
In SQL we join tables based on a key, whereas in NumPy we join arrays by axes.
We pass a sequence of arrays that we want to join to the concatenate() function, along with the axis. If the axis is not explicitly passed, it is taken as 0.

```python
import numpy as np

arr1 = np.array([1, 2, 3])

arr2 = np.array([4, 5, 6])

arr = np.concatenate((arr1, arr2))

print(arr)

```
OUTPUT:
[1 2 3 4 5 6]

## Splitting NumPy Arrays

Splitting is the reverse operation of Joining.
Joining merges multiple arrays into one and Splitting breaks one array into multiple.
We use array_split() for splitting arrays, we pass it the array we want to split and the number of splits.
Split the array into 3 parts:

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5, 6])

newarr = np.array_split(arr, 3)

print(newarr)

```
OUTPUT:
[array([1, 2]), array([3, 4]), array([5, 6])]


## Sorting Arrays

Sorting means putting elements in an ordered sequence.
Ordered sequence is any sequence that has an order corresponding to elements, like numeric or alphabetical, ascending, or descending.
The NumPy ndarray object has a function called sort(), that will sort a specified array.

Sort the array:

```python
import numpy as np

arr = np.array([3, 2, 0, 1])

print(np.sort(arr))
```
OUTPUT:
[0 1 2 3]

## conclusion:
so this was a 1-minute read article on NumPy. Hope this article helps you to get started with NumPy.

Thank you!! 