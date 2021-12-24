---
id: 017-read-file.md
title: First steps in reading files in python
tags:
  - python
  - beginner
  - data
author: Marlene Heinrich
meta-description: Using python to read files
date: 2020-10-27 16:44:28 +0100
keywords: python, beginner, data
template: post
categories:
  - python
image: assets/images/python/read.svg
---

## Reading files in Python

When working with data, it is usually provided as a simple text-file, a
.dat-file or something similar. Reading a file so we can use the data in our
program follows few, simple steps. Nevertheless a lot of things one finds
online may seem really complicated, so we start with a really simple example,
that can be modified easily.

## Writing the datafile "test.dat"

The file we are going to read should be named "test.dat" and saved in the same
folder as this small program. Doing so you should be able to simply copy and
paste the code snippets.

The file should look like this:
```python
x,y
1,1
2,2
3,3
4,4
5,5
6,6
```
## Writing a function read_file

As you usually do not just read one file, we are going to write a function that
takes the name of the file and returns lists with the data.

```python
def get_data(name):                     # first stept of writing a function
    with open(name) as file:            # opens the file we want to read
        data = file.read()              # reads the file
    lines = data.split("\n")            # split into lines after each linebreak
    del lines[0]                        # the first line is "x, y"
    del lines[-1]                       # the last line is empty
    x = list()
    y = list()                          # create empty lists
    for line in lines:
        entry = line.split(",")         # split each line at the comma
        x.append(float(entry[0]))
        y.append(float(entry[1]))       # add data to list
    return x, y                         # ending of the function
```

This is a big bunch of code, but there are only a few important things to
notice: First of all the file is split with "\n" which corresponds to the
linebreak. After that two lines are deleted. Try out what happens if you do
not do that step! After that the lines are split at each ",". If you have
different things where you want to split that is no problem, for example
```python
entry = data.split("\t")
```
splits the lines at a tab. The return statement ends the written function and
gives us the two lists that we have created.

## Using the written function

Now we can use the written function to read the file that we have created in
the beginning. To do so, simply add some code to your Python-file:

```python
x, y = get_data("test.dat") # calls the function with our file
print(x)
print(y)
```

By giving the function a filename we can now read that file and use a
print-statement to check if everything worked as expected.

## Modify this function

If you take a close look at the function, you will notice that you can modify it
for different use. By adding more lists you can work with files with more
entries and as we said before, we can change the characters Python uses to
split a line to many different things.
