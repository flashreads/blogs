---
id: 026-using-argparse
title: Creating a Command-Line Interface Program
tags: Python, cli, args
author: Royce Ayroso-Ong
meta-description: Using argparse to create a simple command line interface program
---

# What is Argparse?

Argparse is a Python package that comes pre-installed when you install Python. It is a module that allows for the creation of user-friendly command-line interfaces.

## Creating a CLI Program to Find the Area of a Rectangle

To start using argparse, you will need to import the pacakge:

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

Then we must create a parser to handle the parsing of command-line arguments along with two positional arguments that we want to extract, i.e. the length and the width of the rectangle.

```python
parser = argparse.ArgumentParser(description='Adds two number arguments together and prints the sum.')

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

**To see our program in action, see example below:**

![Using -h to display help message](https://cdn.discordapp.com/attachments/500822770092081163/772226353188831272/026.PNG | width=100)
![Using argparse to parse two integers](https://cdn.discordapp.com/attachments/500822770092081163/772226648116035604/026b.PNG)



