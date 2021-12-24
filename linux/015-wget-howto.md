---
id: 015-wget-howto.md
title: wget command usage short guide
tags: 
  - linux
  - wget
author: waltherman
meta-description: Downloanding files in different cases with cli tool wget
date: 2021-10-14 04:30:00 +0300 
keywords: linux, wget, download, cli tools
template: post
categories:
  - linux
image: assets/images/download.svg
---

# wget
Wget is a tool for downloading files from the Internet. It supports HTTP, HTTPS and FTP protocols.
It is flexible, so it could be use in background, in scripts, automation.

## wget usage

Syntax is simple:
```
$ wget [options] [URL]
```
And it could be used without any options:
```
$ wget [options] https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.14.12.tar.xz
```
Specify downloaded file name 
```
$ wget -O [filename] [options] [URL]
```
Example:
```
$ wget -O linux.tar.xz https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.14.12.tar.xz
```
Select download destination	
```
$ wget -P [path] [options] [URL]
```
To define download speed use "--rate-limit" construction:
```
$ wget --rate-limit [speed value] [options] [URL]
```
And example with 1 mbps speed limit:
```
$ wget --rate-limit 1m https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.14.12.tar.xz
```
Continue download. Wget is good with downloading via unstable connections, so use "-c" for continue downloading after interruption:
```
$ wget -c [options] [URL]
```
Background download:
```
$ wget -b [options] [URL]
```
Ignore certificate during HTTPS download:
```
$ wget --no-check-certificate [URL]
```
FTP download is possible too:
```
$ wget  --ftp-user=[username] --ftp-password=[password] [FTP URL]
```
