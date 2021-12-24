---
id: 003-python-regex-cheatsheet.md
title: Python Regex Cheat Sheet
tags:
  - python
  - regex
author: Zoran Pandovski
meta-description: The Regular Expression Cheat Sheet [QUICK GUIDE]
date: 2020-05-19 21:38:51 +0200
keywords: python, regex
template: post
categories:
  - python
cover: ../../images/categories/sheet.png
---

We all have been in situations where the Regular Expressions were very useful. This days they are not widely used by programmers but if you still need to verify the strings structure, find and replace strings, working on a new processing utility or just doing regex code wars you will find this sheet helpfull.

# Quantifiers

* `*` - matches 0 or more occurences
* `+` - matches 1 or more occurences 
* `?` - matches 0 or 1 occurences 
* `.` - matches any except newline
* {m} - matches exactly `m`
* {m,n} - matches between `m` and `n`
* {m,} - matches `m `or more
* {,n} - matches up to `n`

# Special characters
* `$` - matches at the end of the string
* `^` - matches the start of the string
* `*?` - matches 0 or more repetitions
* `\` - escape special characters
* [a-z] - matches any lowercase a-z letter
* [^] - matches NOT in the set
* [^ab-d] - matches except a,b,c,d
* m|n - matches either m or n

# Special sequences

* \d - matches digits
* \D - matches non-digits
* \s - matches whitespace
* \S - matches non-whitespace
* \W - matches non-word character
* \w - matches a word character
* \Z - matches only at the end of the string
* \A - matches only at the start of the string

# Groups
* ( ) - matches the group inside parentheses
* (?:A) - matches expression represented by A

For more additional information check [re](https://docs.python.org/3/library/re.html) module documentation.
