---
id: 008-cronjob.md
title: Cron, cron job and crontab
tags:
  - cron
  - cron-job
  - cron-tab
author: subhgogoi
meta-description: What are Cron, cron job and crontab
date: 2020-05-26 21:27:27 +0200
keywords: linux, cron
template: post
categories:
  - linux
image: assets/images/time2.svg
---

# Cron, cron job and crontab

## What are cron, cron job, and crontab?
Cron is a system that helps Linux users to schedule any task. However, a cron job is any defined task to run in a given time period. It can be a shell script or a simple bash command. Cron job helps us automate our routine tasks, it can be hourly, daily, monthly, etc.

Meanwhile, the crontab stands for cron table. It is a Linux system file that contains a list of the cron job. We define our task — bash command, shell script, Python script, etc scheduled in crontab.

## Check cron service on Linux system
```
sudo systemctl status crond.service
```

## Understand a cron job syntax
Cron job syntax on crontab.

* crontab -a <filename>: create a new <filename> as crontab file
* crontab -e: edit our crontab file or create one if it doesn’t already exist
* crontab -l: show up our crontab file
* crontab -r: delete our crontab file
* crontab -v: show up the last time we have edited our crontab file

minute(s) hour(s) day(s) month(s) weekday(s) command(s)

  ![1](https://user-images.githubusercontent.com/23210714/135971402-b24c37db-67fc-4c61-992d-6d11a38eae44.png)

Note: day names 0–6 begin with Sunday.
  
## Handling error on cron job
If the cron job encounters an error, the default, it will send an email to the system administrator.
  
### Send output to a specific file
```
  * * * * * cd /home/abc && /bin/bash shell-script.sh >> log.out
```
The description of the above syntax on a crontab file is as follows:
* The * * * * * means that a task will be executed every minute of every hour of every day of every month and every day of the week
* The directory will be switched to /home/abc where the shell-script.sh is located
* /bin/bash is the path and executable of the Bash shell
* The >> symbol will append the output to an existing file (log.out), while a single > symbol will overwrite the file
* The shell-script.sh is a certain shell script
  
### Use /dev/null
```
  * * * * * cd /home/abc && /bin/bash shell-script.sh > /dev/null 2>&1
```
The description of the commands:
* The > /dev/null tells the cron to redirect the output (STDOUT) to /dev/null
* 2 is the file descriptor for Standard Error (STDERR)
* & is the symbol for file descriptor (without it, the following 1 will be a filename)
* 1 is the file descriptor for Standard Out (STDOUT)

  Note: The 2>&1 tells the cron to redirect all errors (STDERR) to same as standard out (STDOUT)
  
## Write a simple cron automation script
Open our terminal and type **crontab -e** to open a crontab file. Then, scroll down and type the following command.
```
  * * * * * /bin/date >> /tmp/cron_output
```
Check that it is working:
```
tail -f /tmp/cron_output
```
You should see the date updated every minute on the minute (or close to it):
```
Tue Oct  5 12:25:47 IST 2021
Tue Oct  5 12:26:47 IST 2021
```

## Conclusion
The cron job runs on a Linux system to run and execute our regular tasks (terminal commands). The most important thing to learn about the cron job is the bash command on the terminal, how to set our task schedule, and make sure to catch the whole possibilities when our script is running on production, so we can prevent the error.
  
## References
[https://crontab.guru/](https://crontab.guru/)

[https://towardsdatascience.com/create-your-first-cronjob-on-the-linux-server-74e2fdc76e78](https://towardsdatascience.com/create-your-first-cronjob-on-the-linux-server-74e2fdc76e78)
