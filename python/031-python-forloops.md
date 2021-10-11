---
id: 031-python-forloops.md
title: Forloops in Python
tags:
  - python
  - random
author: Hammed Babatunde
meta-description: Using Forloops in Python
date: 2021-10-11 18:38:42 -0700
keywords: python
template: post
categories:
  - python
cover:
---

# What are For Loops?
A for loop acts as an iterator in Python; it goes through items that are in a sequence or any other iterable item. Objects that we can iterate over include strings, lists, tuples, and even built-in iterables for dictionaries, such as keys or values.

## Using For Loops in a List
```python
list1 = [1,2,3,4,5,6,7,8,9,10]
for num in list1:
    print(num) # Prints out each number in list1
```

## Using For Loops in a String 
We've used for loops with lists, how about with strings? Remember strings are a sequence so when we iterate through them we will be accessing each item in that string.
```python
for letter in 'This is a string.':
    print(letter) #print each letter in the string
```

## Using For Loops in Tuples
Tuples have a special quality when it comes to for loops. If you are iterating through a sequence that contains tuples, the item can actually be the tuple itself, this is an example of tuple unpacking. During the for loop we will be unpacking the tuple inside of a sequence and we can access the individual items inside that tuple!
```python
list2 = [(2,4),(6,8),(10,12)]
for tup in list2:
    print(tup) #prints each tuple

# Now with unpacking!
for (t1,t2) in list2:
    print(t1)
```
## Using For Loops in a Dictionary
Cool! With tuples in a sequence we can access the items inside of them through unpacking! The reason this is important is because many objects will deliver their iterables through tuples. Let's start exploring iterating through Dictionaries to explore this further!

```python
d = {'k1':1,'k2':2,'k3':3} #This is a Dictionary in python

for item in d:
    print(item) #This prints out each keys in the dictionary

# Dictionary unpacking for both keys and values
for k,v in d.items():
    print(k)
    print(v) 
```
We have learned how to use for loops to iterate through tuples, lists, strings, and dictionaries.
