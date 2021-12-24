---
id: 010-python-modules.md
title: Python Modules
tags:
  - python
  - modules
  - python-modules
author: Zoran Pandovski
meta-description: Check out what are Python modules and why to use them
date: 2020-06-17 22:56:26 +0200
keywords: python, modules, python-modules
template: post
categories:
  - python
image: assets/images/python/python1.svg
---

Imagine a complex project where you have a lot of code. Having everything written in a single Python file will become un-maintainable, too complex and hard to debug. To have an abstraction layer that will provide separation of the code in different parts that can be reusable would be a great advantage. So, for example, to import one file into another and reuse classes and functions from it. Python already provides that abstraction by using the `modules`. Adding the `import` statement in the Python file means you are using the modules. Let's check that with a simple code example. The following directory contains two Python files:

```
├── modulea.py
├── moduleb.py
```

The `modulea` contains one function e.g

```python
def my_awesome_number(number):
    print(f'The awesome number is {number}'.)
```

Now, let's import `modulea` in `moduleb`

```python
# other imports could be included too e.g 
from random import random # pyhthon module for generating random numbers
# import the modulea
import modulea

def random_number():
    numb = random()
    modulea.my_awesome_print(numb)
```

What happens when we import `modulea` in `moduleb`?

The `import modulea` will look in:
* The same directory for the file with the name `modulea.py`.
* The list of directories in the [PYTHONPATH](https://docs.python.org/3/using/cmdline.html#envvar-PYTHONPATH).
* The installation default directory.

and will raise [`ModuleNotFound`](https://docs.python.org/3/library/exceptions.html#ModuleNotFoundError) error if the `modulea` isn't found. In this example, it will be found and will be executed by the Python interpreter in isolated scope. Next, the `random` module will be executed too and all of the (classes, functions, variables) in our example `my_awesome_number` function from `modulea` will be stored in the module's dictionary and be available for use through the module's namespace. The functions from the imported module will be executed only the first time when the module is imported.
The imported modules as `random` and `modulea` are isolated in the module namespace to avoid the naming collision. 
In short that is what happens when you import the module. So, with the simple words, we can explain the Python modules as files with the suffix `.py` that contains Python statements. They as building blocks will provide code simplicity, better maintainability and reusability, so always prefer to use them. To check all of the available built in Python modules check [Python Module Index](https://docs.python.org/3/py-modindex.html)