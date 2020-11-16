---
id: 001-list-dot-files.md
title: How to list `dot` files in Linux
tags:
  - linux
  - ls
  - list-command
author: Zoran Pandovski
meta-description: How to list all files in a Linux directory
date: 2020-05-26 21:27:27 +0200
template: post
categories:
  - linux
cover: ../images/categories/linux.png
---

The [Unix-like](https://en.wikipedia.org/wiki/Unix-like) operating systems are using `.` to point to the current directory and `..` to point to the parent directory. These entries are not usually the once you are looking when listing the current dir so the `ls` command hides them. But, there are a lot of files that are also starting with `.` which will not be visible too. For e.g run `ls` in a user home:

```bash
ls
```
shall return

```
Desktop
Documents
Downloads
info.txt
csa.py
```

So, there are no `.` files. Many users are pointing to these files as `hidden` files but it is not necessarily true. The original intention was to hide only `.` and `..` but it was intentionally left to not list the other files too, since the community users find it more useful to name the files that are used for caching, configuration, preferences etc using the `.`. If you need to list those files too just add `-a` or `-all` flag to the `ls` command.

```bash
# do not ignore entries starting with .
ls -a, --all
```

shall return

```
Desktop
Documents
Downloads
info.txt
csa.py
.gradle
.Skype
.zoom
```