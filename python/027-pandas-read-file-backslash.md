---
id: 027-pandas-unicodeescape-error.md
title: Pandas read files
tags:
  - python
  - pandas
author: Matteo Buldrini
meta-description: How to read in Pandas files that give you unicodeescape error.
date: 2020-12-20 14:30:05 +0200
keywords: python, pandas
template: post
categories:
  - python
image: assets/images/python/python3.svg
---

Sometimes when reading a file in Pandas you may incur in the following error after declaring the path name:

```python
  SyntaxError: (unicode error) ‘unicodeescape’ codec can’t decode bytes in position 2-3:
  truncated \UXXXXXXXX escape.
```

This happens because path names tend to have backslashes in them (e.g. 'C:\Documents\File.csv'). In Python, backslash is used to signify special characters, but when we use it in a path name we want to refer to actual backslashes, not to special characters.

To solve this issue, you need to add an <b>r</b> before the path name, so that Python can interpret backslashes as strings.

Example:

```python
df = pd.read_csv(r'C:\Documents\File.csv')
```
