---
id: 011-compress-uncompress-files-in-linux.md
title: How to compress and uncompress files in linux.
tags:
  - linux
  - compress
  - uncompress
  - tar
  - gzip
  - gunzip
author: Partha Talukdar
meta-description: Learn how to compress and uncompress files in Linux.
date: 2021-10-01
keywords: linux, gzip, compress, uncompress.
template: post
categories:
  - linux
cover: ../../images/categories/linux.png
---

# Compressing , Uncompressing Files In Linux?

The most commonly used commands in linux are tar, gzip and gunzip for compressing and uncompressing files in linux.

# Tar vs Gzip

The tar command is used to compress a group of files into an archive. The command is also used to extract or modify tar archives as well.
The tar command does not necessarily compresses the files in the archive it just groups them into a single file. To achieve compression and reduce disk usage on your linux systems the gzip option can be used with tar.


## Basic Syntax For Tar?

```
tar [options] [archive-file] [file or directory to be archived]

```
### Options For Tar?

```
-c : Creates archive
-x : Extracts the archive
-f : creates archive with given filename
-t : displays or lists files in archived file
-u : archives and adds to an existing archive file
-v : Displays verbose information
-A : Concatenates the archive files
-z : compresses the tar file using gzip
-j : compresses the tar file using bzip2
-W : Verifies an archive file
-r : updates or adds file or directory in already existing .tar file

```
## Example Usage Of Tar and Gzip:

* Extract an archive:
```
$tar xfv archive.tar

```
(Options: x = extract, f = file, v = verbose)

* Create an archive with files or folder:
```
$tar cfv archive.tar file1 file2 file3

```
(Options: c = create)

* Create compressed archives with tar using gzip:
```
tar cfzv archive.tar file1 file2 file3

```
(Options: z = compress with gzip)

* Extract files from gzip tar Archive archive.tar.gz:
```
$tar xvzf archive.tar.gz

```
(Options: x = extract, f = file, v = verbose)


## More Useful Resources:
[Create Tar GZ File](https://linuxize.com/post/how-to-create-tar-gz-file/)

[Tar in linux](https://www.tecmint.com/18-tar-command-examples-in-linux/)

[Tar Examples](https://www.interserver.net/tips/kb/use-tar-command-linux-examples/)
