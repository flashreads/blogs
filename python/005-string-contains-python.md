---
id: 005-string-contains-python.md
title: Check if a string contains substring in Python
tags: string, contains, python, python3
author: Pavle Jonoski
meta-description: What to use to check if a string contains a substring in Python
---

# String `contains` method in Python

Python's alternative to `String.contains` is the keyword `in`.

```python

foobar = 'foobar'
substr = 'foo'

if substr in foobar:
    print('Yes')
else:
    print('No')

# Prints 'Yes'
```

Although under the hood Python may use some of the [magic methods](https://docs.python.org/3/reference/datamodel.html#special-method-names) like
[`__contains__`](https://docs.python.org/3/reference/datamodel.html#object.__contains__), `__iter__` and `__getitem__`, you should try to avoid using
these methods directly on strings. These are useful when defining your own type
with testing membership capabilities.
