---
id: 039-__add__()-method.md
title: __add__() in Python
tags:
  - python
  - random
author: Tarun K Kumar
meta-description: __add__() magic method in python
date: 2022-10-24 20:52:00 +0530 
keywords: python
categories:
  - python
image: assets/images/python/python3.svg
---
# __add__() Method

The `_-add__` method is what enables operator overloading in python objects. Operator overloading is when you explicitly tell an object what to do when a certain operator is used.

The `__add__` method enables us to overload the `+` operator of an object.

Let us try to add a Python integer with a user-defined Number Object. If you try to add an object and an integer organically like this

```python
class Number:
    def __init__(self, value):
        self.value = value

num = Number(5)

print(num + 5)
```
You would get:
```bash
Traceback (most recent call last):
  File "main.py", line 7, in <module>
    print(num + 5)
TypeError: unsupported operand type(s) for +: 'Number' and 'int'
```
Python throws an error because the `int` class is not compatible with our newly created `Number` class. To enable our intended feature, we can make use of the `__add__()` dunder method inside the `Number` class to perform the addition.
```python
class Number:
    
    def __init__(self, value):
        self.value = value
        
    def __add__(self,value):
        return self.value + value

num = Number(5)

print(num + 5)
```
-The `__add__` method accepts 2 arguments, `self` and `value` where `self` is a mandatory positional argument that is a reference to the current object and is on the left-hand side of the `+` operator.
-The `value` argument is the value that is on the right-hand side of the `+` operator.
-We return an integer that adds the object's value and the right-hand side operand.
```bash
10
```
But if we reverse the order of the operands it throws and error:
```python
print(5 + num)
```
The output:
```bash
File "main.py", line 14, in <module>
    print(num + 5, 5 + num)
TypeError: unsupported operand type(s) for +: 'int' and 'Number'
```
To remedy this, we can use the `__radd__()` method which provides support for said reversal of operands.

```python
class Number:
    
    def __init__(self, value):
        self.value = value
        
    def __add__(self,value):
        return self.value + value
        
    def __radd__(self,value):
        return self.value + value

num = Number(5)

print(num + 5, 5 + num)
```
The output
```bash
10 10
```
With this we have successfully overloaded the `+` operator in Python. I hope this article was useful. Thank you for reading.

