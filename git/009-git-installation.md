---
id: 009-git-installation.md
title: Git Installation
tags:
  - Git
  - Github
  - Git First Time
  - Git Installation
author: Sid-Lais
meta-description: Git for first time
date: 2021-10-11 08:30:00 +0100
keywords: Git, Github
template: post
categories:
  - git
image: assets/images/setup.svg
---

# Git Installation
Before working on Git repositories it is advised to get a good knowledge of Git. Git is an open source version control system. It is easy to learn and has very fast performance irrespective of the system.

## Steps to install Git

1. Download and install [Git](https://git-scm.com/) for your system.
2. After installation open a terminal in your system and write **git** to check proper installation.
<br>
If it returns something like this below then congrats. *Git has been installed*.
<img src="https://user-images.githubusercontent.com/40291960/136825925-cfeccd43-78a9-4eb1-a485-00b9110fc4be.png" height=300>

## Set up Git credentials

1. In the terminal/shell type:

```bash
git config --global user.name "Your name here"
git config --global user.email "your_email@example.com"
```
These will configure the git to set your name and email as default.

You can also add(optional):

```bash
git config --global color.ui true
git config --global core.editor emacs 
```

The first command is to enable colors in the terminal which are used to better understand the current state of the code.

The second command is to change the default text editor to emacs. You can change "emacs" to any other text editor desired.

## For more information refer to [GitHub Docs](https://docs.github.com/en/get-started/quickstart/set-up-git)