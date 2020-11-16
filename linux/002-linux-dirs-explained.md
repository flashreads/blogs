---
id: 002-linux-dirs-explained.md
title: Linux directories structure explained
tags:
  - linux
  - linux-directoy
  - bin
  - etc
  - dev
  - root
  - home
  - lib
  - sbin
author: Zoran Pandovski
meta-description: High level explanation of Linux directory structure and file system hierarchy
date: 2020-05-28 14:56:59 +0200
keywords: linux, linux-directoy, bin, etc, dev, root, home, lib, sbin
template: post
categories:
  - linux
cover: ../../images/categories/linux.png
---

This short article aims to provide a simple and useful explanation to the Linux directory structure.

![Linux dirs](https://media.geeksforgeeks.org/wp-content/uploads/linuxDir.jpg)

* `/` - This is the top level root directory, that contains all other directories on the system.
* `bin` - This directory contains all the essential binary executable programs, required for booting, shells like cp, ls, grep, kill, [vi text editor](https://en.wikipedia.org/wiki/Vi) etc.
* `boot` - All of the static files used in booting the system are located here e.g [grub](https://en.wikipedia.org/wiki/GNU_GRUB), [vmlinux](https://en.wikipedia.org/wiki/Vmlinux)
* `cdrom` - It is not part of the Filesystem hierarchy standard but can be found usually in Ubuntu. It is used as a temporary location for CD-ROMs.
* `dev` - Files related to the hardware as cdrom, cpu, drive can be found here. Also some pseudo-devices as `dev/null`.
* `etc` - Host-specific system configuration files.
* `home` - This is the home directory for each user on the system e.g /home/user1, /home/user2 that contains configurations per user.
* `lib` - All of the shared library images and kernel modules needed by /bin and /sbin.
* `lost+found ` - All of the unlinked, corrupted files used to recover by [fsck](https://en.wikipedia.org/wiki/Fsck) are placed here.
* `media` - All of the removable media as CD, USB when plugged into the system are mounted inside the media directory.
* `mnt` - This is used for a temporary mounting file system.
* `opt` - This directory contains optional packages and third party applications.
* `proc` - It contains the information related to the running processes.
* `root` - The home directory for the root user.
* `sbin` - Similar directory as /bin that contains essential binaries for system administration.
* `srv` - This directory contains most of the service related or files specific to servers.
* `sys` - The virtual file system.
* `usr` - All of the files used by the users, not by the system are saved in this directory.
* `var` - It contains most of the variable data files as logs, mails, temp files.

