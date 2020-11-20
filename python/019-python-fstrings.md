---
id: 019-python-fstrings.md
title: f-Strings - A nice way of formatting strings
tags:
  - python
  - beginner
  - strings
author: Durval Carvalho
meta-description: Using python to formatings strings
date: 2020-10-27 15:35:41 -0300
keywords: python, beginner, strings
template: post
categories:
  - python
cover: ../../images/categories/python.png
---

## Formatting Strings

Creating dynamic texts is a common need in almost any programming language. Python offers a number of ways to create dynamic text and the coolest one is called f-strings

## The not-so-cool way

Python during its creation had influences from other languages (like C), so it inherited the parser mechanism that runs through a string looking for specific symbols (like %d, %s, %f, for integers, strings and floats respectively).
Fortunately in python it is simpler, there is only one symbol for all types of variables, but even so it is not as cool as f-strings

```python

name = "Lebron James"
age = 35
height = 2.06

print("Hey people! My name is %s, I'm %s years old and I'm %s meters tall" % (name, age, height))
```

## The super cool way

Starting with python version 3.6, f-strings were built into python. f-string comes is an abbreviation for "formateed strings literals".

Its syntax is quite simple and intuitive (and much cooler). Just put an f before the strings and identify the variables within the string body

```python

name = "Lebron James"
age = 35
height = 2.06

print(f"Hey people! My name is {name}, I'm {age} years old and I'm {height} meters tall")
```

As you can see, this way of creating dynamic strings is more readable, and such more cooler!

If you are interested, try to research other details about the f-strings such as the use of arbitrary expressions, multiline expressions, the f-string performance. You will love!
