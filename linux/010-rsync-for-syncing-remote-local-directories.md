---
id: 010-rsync-for-syncing-remote-local-directories.md
title: How to synchronize remote and local directories using rsync.
tags:
  - linux
  - rsync
  - synchronization
author: Partha Talukdar
meta-description: Rsync is a remote and local file synchronization tool for syncing linux systems.
date: 2021-10-01
keywords: linux, rsync, synchronization, local remote directories.
template: post
categories:
  - linux
image: assets/images/sync.svg
---

# What is Rsync?

Rsync stands for “remote sync” which is a remote and local file synchronization tool. It is based on an algorithm that minimizes the amount of data copied/synced by only moving the particular files that have changed.
Rsync is a very flexible network-enabled syncing tool. Due to its ubiquity on Linux and Unix-like systems and its popularity as a tool for system scripts, it is included on most Linux distributions by default.


## Basic Syntax?

The basic syntax of rsync is similar to scp , ssh and cp.

## Syncing Local Systems?

To sync files on the same system the below command can be used:

```
$rsync -r <dir_name>/ <dir_name>

```
eg. If we want to synchronize Dir1 to Dir2 recursively the command would go as follows:

```
$rsync -r Dir1/ Dir2
```
r stands for recursively.
Instead of using -r we can use the -a flag which is most commonly used. The -a option is kind of a combination flag. It stands for “archive” and syncs recursively and preserves symbolic links, special and device files, modification times, group, owner, and permissions.

Syntax:

```
$rsync -a <dir_name>/ <dir_name>

```
Example:

```
$rsync -a Dir1/ Dir2

```
Note: The trailing / in Dir1 is required to place all the contents inside Dir1 to Dir2 if / is not provided Dir1 will be placed in Dir2 and hierarchy will be as 

$~/Dir2/Dir1/files

## For Verbose details of what is being synced ?

To know more about what files are being synced from a directory to another we can pass 'v' flags which means verbose as follows:

```
$rsync -av <dir_name>/ <dir_name>

```
## Syncing files to remote systems ?

Rsync can be used to transfer files and synchronize one linux server to another the only prerequisite is to have ssh access to the systems and also rsync needs to be installed on both the systems.Once SSH access verified between the two machines rsync can be performed from one system to another.

### Example 1 Rsync From Local to remote host:

```

$rsync -a ~/dir1 username@remote_host:destination_directory

```
### Example 2 Rsync From Remote to local host:

```

$rsync -a username@remote_host:/home/username/dir1 place_to_sync_on_local_machine

```
Like cp and similar tools, the source is always the first argument, and the destination is always the second.

# Conclusion

Rsync makes it a good option for many different file-level operations.Rsync can simplify file transfers over networks and add robustness to local directory syncing. 

# Useful Resources:

[How to use Rsync](https://linuxize.com/post/how-to-use-rsync-for-local-and-remote-data-transfer-and-synchronization/)
[10 practical examples of rsync](https://www.tecmint.com/rsync-local-remote-file-synchronization-commands/)







