---
id: 026-using-argparse
title: Creating a Command-Line Interface Program With Argparse
tags:
  - Python
  - cli
  - args
  - argparse
author: Royce Ayroso-Ong
meta-description: Using argparse to create a simple command-line interface program
date: 2020-10-31 19:07:19 -0400
template: post
categories:
  - python
cover: ../images/categories/python.png
---

# What is Argparse?

[Argparse](https://docs.python.org/3/library/argparse.html) is a module that comes pre-installed when you install Python. It allows for the creation of user-friendly command-line interfaces.

## Creating a CLI Program to Find the Area of a Rectangle

<img src="https://cdn.discordapp.com/attachments/500822770092081163/772226648116035604/026b.PNG" alt="Using argparse to parse two integers" width="550">


To start using argparse to recreate the example above, you will need to import the pacakge:

```python
# the following code will be contained within a file called area.py
import argparse
```

Now we will create a simple method to multiply and return two numbers, like so:

```python
def area_of_rectangle(length, width):
    return length * width
```

This method will be called when the program is executed. The parameters `length` and `width` will be extracted from the command line arguments.  

Now we must create a parser to handle the parsing of command-line arguments along with two positional arguments that we want to extract, i.e. the length and the width of the rectangle.

```python
parser = argparse.ArgumentParser(description='Calculates the area of a rectangle')

parser.add_argument('length', default=0, type=int, help='An integer for the length of the rectangle')
parser.add_argument('width', default=0, type=int, help='An integer for the width of the rectangle')
```

We can use the values of these arguments by calling upon `parser.parse_args()`.

```python
args = parser.parse_args()
area = area_of_rectangle(args.length, args.width)
print('The area of your rectangle is: ', area, ' units squared.')
```

Putting everything together should look like this:

```Python
# area.py
import argparse

def area_of_rectangle(length, width):
    return length * width

parser = argparse.ArgumentParser(description='Calculates the area of a rectangle')

parser.add_argument('length', default=0, type=int, help='An integer for the length of the rectangle')
parser.add_argument('width', default=0, type=int, help='An integer for the width of the rectangle')

args = parser.parse_args()
area = area_of_rectangle(args.length, args.width)
print('The area of your rectangle is: ', area, ' units squared.')
```

Thats about it! Argparse will now parse your command-line agruments for integers to be used in our method. Every parser will have a `-h` optional argument by default; this option will display the help message along with the parser's description.

<img src="https://cdn.discordapp.com/attachments/500822770092081163/772226353188831272/026.PNG" alt="Using -h to display help message" width="550">
