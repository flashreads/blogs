---
id: 008-list-index.md
title: How to find the index of an element in a list
tags:
  - python
  - lists
  - list-index
author: Zoran Pandovski
meta-description: Finding the index of an item in a list in Python with examples
date: 2020-06-05 21:13:49 +0200
keywords: python, lists, list-index
template: post
categories:
  - python
image: assets/images/python/queue.svg
---

The [`list.index` method](https://docs.python.org/3/tutorial/datastructures.html#data-structures) will return the index of the first found element in the list for e.g

```python
numbers = [1,2,2,2, 3,4,5,6,7]
numbers.index(2)
>>>1
```

So, in this case, there are 3 elements with value 2 but the index method returns only the first one. If the value is not found `index` method will raise a [ValueError](https://docs.python.org/3/library/exceptions.html#ValueError).

```python
numbers = [1,2,2,2, 3,4,5,6,7]
numbers.index(45)
>>> ValueError: 45 is not in list
```

The `index` method will check every element in the list until it finds a match. That means it has O(n) complexity. In the cases where you have a very long list, you can consider using the start or end optional parameters to the `index` for e.g

```python
numbers = [1,2,3,4,5,6,7,8,9,10,11,12]
# find index of 11 starting from 9th element
numbers.index(11, 9)
>>>10
```