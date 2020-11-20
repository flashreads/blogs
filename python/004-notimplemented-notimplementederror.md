---
id: 004-notimplemented-notimplementederror.md
title: NotImplemented vs NotImplementedError in Python
tags:
  - python
  - exceptions
author: Zoran Pandovski
meta-description: The difference between NotImplemented and NotImplementedError in python
date: 2020-05-26 21:27:54 +0200
keywords: python, exceptions
template: post
categories:
  - python
cover: ../../images/categories/python.png
---

# What is NotImplemented?

The NotImplemented is built in constant in Python. It should be used by some of the python special methods for e.g (__add__(), __eq__()) to address that the operation is not implemented but can be run by other type. If this sounds confusing let's preview the use case of NotImplemented inside the python datetime standard library.

```python
 def __add__(self, other):
        if isinstance(other, timedelta):
            # for CPython compatibility, we cannot use
            # our __class__ here, but need a real timedelta
            return timedelta(self._days + other._days,
                             self._seconds + other._seconds,
                             self._microseconds + other._microseconds)
        return NotImplemented
```
The first line checks if the other object is timedelta, and if it is, it will return timedelta object that contains the time, seconds and microseconds of both objects. But if the other object is not timedelta, it doesn't throw an exception because, maybe the other object will know how to handle this operation. So, in short words the interpreter will try the __add__ operation on the other type. If both attempts returne NotImplemented, then the appropriate exception will be raised.


# The NotImplementedError exception

This is an exception that derives from the [RuntimeError](https://docs.python.org/3/library/exceptions.html#RuntimeError). The usual use case of this exception is in the abstract class methods when they required the derived class to override them. 

```python
class Foo():

    @property
    def some_method(self):
        raise NotImplementedError("The derived class should implement the logic.")
```

Also, while developing you can raise this exception as a reminder to implement this method in the future. 

```python
class Foo():

    #TODO
    def new_method(self):
        raise NotImplementedError("Still not implemented.")
```