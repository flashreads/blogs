---
id: 034-python-functions.md
title: Creating functions in Python
tags:
  - python
  - random
author: Hammed Babatunde
meta-description: Creating functions in python 
date: 2021-10-17 18:38:42 -0700
keywords: python
template: post
categories:
  - python
cover:
---

# What is a Function in Python 
Formally, a function is a useful device that groups together a set of statements so they can be run more than once. They can also let us specify parameters that can serve as inputs to the functions.

On a more fundamental level, functions allow us to not have to repeatedly write the same code again and again. If you remember back to the lessons on strings and lists, remember that we used a function len() to get the length of a string. Since checking the length of a sequence is a common task you would want to write a function that can do this repeatedly at command.


## def Statements
Let's see how to build out a function's syntax in Python. It has the following form:
```python
def name_of_function(arg1,arg2):
    '''
    This is where the function's Document String (docstring) goes
    '''
    # Do stuff here
    # Return desired result
```

## Example 1: A simple print 'hello' function
```python
def say_hello():
    print('hello')

#Call the Function
say_hello()
```

## Example 2: A simple greeting function
Let's write a function that greets people with their name.
```python
def greeting(name):
    print('Hello %s' %(name))

greeting('Jose')  #calling the function
```

## Using return
Let's see an example that use a return statement. return allows a function to return a result that can then be stored as a variable, or used in whatever manner a user wants.
```python
import math

def is_prime2(num):
    '''
    Better method of checking for primes. 
    '''
    if num % 2 == 0 and num > 2: 
        return False
    for i in range(3, int(math.sqrt(num)) + 1, 2):
        if num % i == 0:
            return False
    return True
```

Great! You should now have a basic understanding of creating your own functions to save yourself from repeatedly writing code!
