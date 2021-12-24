---
id: 018-write-file.md
title: First steps in writing files in python
tags:
  - python
  - beginner
  - data
author: Marlene Heinrich
meta-description: Using python to write files
date: 2020-10-27 16:44:28 +0100
keywords: python, beginner, data
template: post
categories:
  - python
image: assets/images/python/file.svg
---

## Writing files in Python

Working with data, it is often useful not just to read files, but also to be
able to write data to files. Here we are going to discuss a first simple
approach on how to write data, that we have saved in lists to a file.

## Create the data

Imagine, that you have read data from a file and calculated some new stuff, that
you have saved in two lists:

```python
x = [1, 2, 3, 4, 5, 6, 7]
y = [7, 6, 5, 4, 3, 2, 1]
```
Now we want to write these to lists to a file, so we can forget about them for
a few weeks and then use a read-function and continue working again. A file we
are interested in might look something like this:

```python
x,y
1,7
2,6
3,5
4,4
5,3
6,2
7,1
```

## Write code that creates a file

The easiest code to create and write a file looks like this:

```python
with open("testfile.dat", "w") as file:
    file.write("x,y\n")
    for i in range(len(x)):
        file.write(str(x[i]) + "," + str(y[i]) + "\n")
```

The first line opens a file named "testfile.dat". The "w"-statement opens a
file and overwrites content. If we swap it for "a" the new content will be
appended to the file. Try that one out to see the difference! The first write
statement just creates a nice heading for our file, while the rest of the file
is written in a loop and adds the data.

The single entries have to be given as strings, so the float (or whatever) has
to be converted. If you are not sure about the different outcome of
```python
str(x[i])
```
and
```python
"x[i]"
```
try both out so it does not go wrong in an important moment.

Different to reading a file in Python it is not super easy to write a function to
write data to a file that
fits all needs. But try out some different options to save your data in the
python-program and you will find an option that suits your needs. And the
general structure usually does not change, so you will be able to go a long way
with the few lines you learned here!
