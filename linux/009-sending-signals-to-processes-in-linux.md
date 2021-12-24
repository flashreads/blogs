---
id: 00-sending-signals-to-processes-linux.md
title: Sending Signals For Controlling Processes In Linux.
tags:
  - linux
  - process management
  - controlling processes by sending signals
author: Partha Talukdar
meta-description: How to control processes in linux by sending signals.
date: 2021-10-01
keywords: linux, process management, signals
template: post
categories:
  - linux
image: assets/images/signal.svg
---

# Sending Signals In Linux

The most basic approach of controlling processes in linux is by sending signals to the processes.There are multiple signals that can be sent to a process.There are multiple signals that can be sent to a process.Simply run below command to view all the available signals:

`kill -l`
 
To send signals to a process we can use kill, pkill and pgrep commands in linux.

## Finding Process IDs in Linux ?

PS is the most common used command in linux to view all active processes in linux, use the below commands to view the process:

To view all processes:

```
$ps

OR

$ps aux

```

To find a particular process PID:

```
$pidof <application_name>

OR

$ps -ef | grep <application_name>

```
example:

```
$pidof java
26901

OR

$ps -ef | grep java

```


## Common signals in linux ?

Most signals in linux are for internal use by the system, or for system administrators when they perform any server operation or developer when they write code. The following are signals which are useful for a system user:
```
SIGHUP 1 – sent to a process when its controlling terminal is closed.
SIGINT 2 – sent to a process by its controlling terminal when a user interrupts the process by pressing [Ctrl+C].
SIGQUIT 3 – sent to a process if the user sends a quit signal [Ctrl+D].
SIGKILL 9 – this signal immediately terminates (kills) a process and the process will not perform any clean-up operations.
SIGTERM 15 – this a program termination signal (kill will send this by default).
SIGTSTP 20 – sent to a process by its controlling terminal to request it to stop (terminal stop); initiated by the user pressing [Ctrl+Z].

```


The following are kill commands examples to kill a java application using its PID (ProcessId) once it freezes or becomes unresponsive:

```
$pidof java 
26901

$kill 9 26901
OR

$kill -KILL 26901
OR

$kill -SIGKILL 26901
```

To kill an application using its name, use pkill or killall like so:

```
$pkill java

$killall java
```
## Some useful references:

[Find PID In Linux](https://www.tecmint.com/find-process-name-pid-number-linux/)

[Find Linux Process Memory Ram Cpu Usage](https://www.tecmint.com/find-linux-processes-memory-ram-cpu-usage/)

[Find Processes By Memory](https://www.tecmint.com/find-processes-by-memory-usage-top-batch-mode/)
