---
id: 038-dictionary-comprehension.md
title: Dictionary Comprehension in Python
tags:
  - python
  - random
author: Tarun K Kumar
meta-description: dictionary comprehension in python
date: 2022-10-24 21:53:39 +0530 
keywords: python
categories:
  - python
image: assets/images/python/python3.svg
---
# Dictionary Comprehension in Python

Dictionary comprehension is a simple method of creating a dictionary without using the dict() method and is similar to the list comprehension concept. Suppose we have a list of keys and list of corresponding values and we want to turn those into a dictionary, then we would usually write something like:  

```python
keys = ['animal','plant','insect']
values = ["dog","lemongrass","Weevil"]

dict = {}

for i in range(len(keys)):
    dict[keys[i]] = values[i]

print(dict)
```
which would print:
```python
{'animal': 'dog', 'plant': 'lemongrass', 'insect': 'Weevil'}
```
Well, we have our end result but the same can be achieved with less code. This is where dictionary comprehension comes in.

The refactored code:
```python
keys = ['animal','plant','insect']
values = ["dog","lemongrass","Weevil"]

print({keys[i]:values[i] for i in range(len(keys))})
```
So, lets breakdown that line:

To use dictionary comprehension, a dictionary must be created using `{}` and the following syntax must be followed:
```python
dictionary = {key: value for vars in iterable}
```
- The `key` and `values` are our lists containing our key:value pairs where we use `i` as indices to populate our dictionary

You can also use conditionals in dictionary comprehension as well:
```python
keys = ['animal','plant','insect']
values = [-1,2,3]

print({keys[i]:values[i] for i in range(len(keys)) if values[i]>0})
```
The output:
```python
{'plant': 2, 'insect': 3}
```
This is a more pythonic and my favourite way of creating dictionaries in python. I hope this article was useful. Thank you for reading.

