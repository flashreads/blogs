---
id: 012-object-not-subscritble.md
title: TypeError 'NoneType' object is not subscriptable
tags:
  - python
  - python3
  - type-error
  - list
  - dict
author: Zoran Pandovski
meta-description: How to easily resolve the object is not subscriptable error in Python
date: 2020-06-17 22:56:36 +0200
template: post
categories:
  - python
cover: ../images/categories/python.png
---

This error is quite self-descriptive: 

```python
Traceback (most recent call last):
  File "users.py", line 25, in <module>
    user = users[0]
TypeError: 'NoneType' object is not subscriptable
```

It means that you are trying to subscript (index) the object that actually is None. In the above example, the `users` list is empty so you can't get the first user from it since None object doesn't define the [`__getitem__`](https://docs.python.org/3/reference/datamodel.html#object.__getitem__) method. This simply can be fixed by finding out `Why the list is None`.