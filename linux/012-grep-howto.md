---
id: 012-grep-howto.md
title: Grep command usage cheatsheet
tags: 
  - linux
  - grep
author: waltherman
meta-description: Grep is an ultimate command to search text patterns in files
date: 2021-10-13 03:30:00 +0300 
keywords: linux, grep, searching in files
template: post
categories:
  - linux
cover: ../../images/categories/linux.png
---

# What is Grep?

Grep stands for "global regular expression print" and it is an ultimate command to search text or any file for lines that contain a match to the specified text pattern, word or regex.
By default, grep outputs only the matched lines.

## Basic grep usage

```
$ grep pattern filename
```

As a result grep would give all patterns found in file named "filename". For example:

```
$ grep pattern filename
pattern
pattern1
zzzpattern44
```

Also you could use pipe to filter output of any command. For example, let's find installed PostgreSQL client version on Ubuntu server via next command:
```
$ dpkg --list | grep postgresql-client

```

-i parameter used for case-insensetive grep 
```
$ grep -i pattern filename

```
-v - inverted match of grep

```
$ grep -v pattern filename

```

-w used for search only for words match. For example file named "filename" from very first example had several matches, but with this argument there would be only one:
```
$ grep -w pattern filename
pattern
```

Recursive search
Let's find all files matching pattern in this directory and all subdirectories by -r/R argument:

```
$ grep -R pattern .

```
Also we could use grep to find file by its content:

```
$ grep -rnw '/path/to/somewhere/' -e 'pattern'

```
