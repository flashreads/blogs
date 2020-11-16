---
id: 003-Create-and-remove-dir.md
title: How to create and remove directory in linux.
tags:
  - linux
  - mkdir(make-dir) and rmdir(remove-dir command) command
author: Sourabh Yadav
meta-description: How to create and remove a directory in linux
date: 2020-10-28 12:51:54 +0530
template: post
categories:
  - linux
cover: ../images/categories/linux.png
---
The `mkdir` command is used to create a new directory. The command can also be used to create multiple and nested directories too.

`mkdir` command Syntax:

```bash
mkdir   Directory_Name
```
Example: 
```bash
mkdir   Directory1
```
use the `ls` command mentioned in [001-list-files-with-dot.md](linux/001-list-files-with-dot.md) file and you will see  the directory is created.

shall return

```
Directory1
```
Let's make multiple directories at once. To do so we will use the mkdir command with space after every directory name.

```bash
mkdir   Dir1 Dir2 Dir3
```

shall return

```
Dir1 Dir2 Dir3 
```
To create parent directories using the `mkdir` command and pass the `-p` option. By using this option you can create a nested directory. 

```bash
mkdir -p Dir_out/Dir_in/Last
```

shall return

```
Dir_out
└── Dir_in
    └── Last
```

The `rmdir` command is used to remove a directory(it is like the delete folder option in windows) the directory deleted using the `rmdir` command can not be restored again. This command can not be used to remove 
a directory with files and sub directory inside them, To do so we use the `rm` command 

`rmdir` command Syntax:

```bash
rmdir   Directory_Name
```
Example: let's suppose we have created three directory  by using `mkdir Dir1 Dir2 Dir3` now we will remove the Dir1.

```bash
rmdir   Dir1
```
shall return

```
Dir2 Dir3 
```
To delete a directory having more directories and files inside them we use the `rm` command with `-r` option. Let's have two directory Dir1 and  Dir_out having Dir_in, inside 
it. If we use the `rmdir` command To remove the Dir_out it will give you an error as Directory not empty. To delete it we use the rm command. 

`rm` command Syntax:

```bash
rm -r  directory_name
```


```bash
rm -r  Dir_out
```

shall return

```
Dir1
```

