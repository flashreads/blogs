---
id: 004-reading-linux-file-permissions.md
title: Linux File Permissions
tags:
  - linux
  - file permissions
author: Calista Lai
meta-description: how to read file/directory permissions in linux
date: 2020-10-31 01:32:22 -0700
keywords: linux, file permissions
template: post
categories:
  - linux
cover: ../../images/categories/linux.png
---

# File Permissions

File permissions determine who can read, write, or execute a file. In Linux, 
these details can be viewed by using the `ls -l` command. 

On the very left of the list, you will see text that looks similar to this:

`-rwxrw-r--`

These are your file permissions.

## What do These `rwx-` Characters Mean?

* `r` read - user is allowed to view the file's contents
* `w` write - user is allowed to edit the file's contents
* `x` execute - user is allowed to execute the file (or in the case of a directory, view its contents)
* `-` no permission - used in place when a permission is not granted

## File type
The very first character specifies the file type. In this case, `-` indicates a regular file. Different characters represent different types:
* `b` block device
* `c` character device
* `d` directory
* `l` symbolic link
* `p` named pipe
* `s` socket file

## Owner, Groups, and Others

The next nine characters determine what permissions the owner, groups in ownership, and other users have.

The first three characters after the file type indicate the ower's permissions. In `-rwxrw-r--`, the owner's file permissions are `rwx`. They are allowed to read, 
write, and execute the file.

The following three characters determine permissions for members of groups that own the file. In this case, group permissions are `rw-`. They are allowed to 
read and write to the file, but cannot execute it.

The last three characters are permissions for all other users that do not fit into the previous two categories. This example's permissions for other users are
`r--`. They are only allowed to read the file.

## Diagram:

![diagram](https://www.comentum.com/images/permissions.jpg)
