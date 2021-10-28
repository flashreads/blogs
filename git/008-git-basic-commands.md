---
id: 008-git-basic-commands.md
title: Most Used Commands of Git
tags: 
  - git
  - git cheat sheet
  - git-commands
  - github
date: 2021-10-07 10:53:39  
keywords: Git, Github
template: post
categories:
  - git
cover: ../../images/categories/git.png
author: Juhi Vishwakarma
meta-description: list of frequently used git commands
---

# Git commands Cheat Sheet

to check your Git configuration:  
```bash
git config -l
```

to setup your Git username:  
```bash
git config --global user.name "name"
```

to setup your Git user email:  
```bash
git config --global user.email "signups@fabiopacifici.com"
```

to cache your login credentials in Git:  
```bash
git config --global credential.helper cache
```

to initialize a Git repo:  
```bash
git init
```

to add a file to the staging area in Git:  
```bash
git add filename_here
```

to add all files in the staging area in Git:  
```bash
git add .
```

to add only certain files to the staging area in Git:  
```bash
git add fil*
```

to check a repository's status in Git:  
```bash
git status
```

to commit changes in the editor in Git:  
```bash
git commit
```

to commit changes with a message in Git:  
```bash
git commit -m "your commit message here"
```

to commit changes (and skip the staging area) in Git:  
```bash
git commit -a -m"your commit message here"
```

to see your commit history in Git:  
```bash
git log
```

to see your commit history including changes in Git:  
```bash
git log -p
```

to see a specific commit in Git:  
```bash
git show commit-id
```

to see log stats in Git:  
```bash
git log --stat
```

to rename files in Git:  
```bash
git mv oldfile newfile
```

to revert staged changes in Git:  
```bash
git reset HEAD filename
git reset HEAD -p
```

to create a new branch in Git:  
```bash
git branch branch_name
```

to switch to a newly created branch in Git:  
```bash
git checkout branch_name
```

to list branches in Git:  
```bash
git branch
```

to create a branch in Git and switch to it immediately:  
```bash
git checkout -b branch_name
```

to delete a branch in Git:  
```bash
git branch -d branch_name
```

to merge two branches in Git:  
```bash
git merge branch_name
```

to add a remote repository in Git:  
```bash
git add remote https://repo_here
```

to see remote URLs in Git:  
```bash
git remote -v
```

to push changes to a remote repo in Git:  
```bash
git push
```

to pull changes from a remote repo in Git:  
```bash
git pull
```

to merge a remote repo with your local repo in Git:  
```bash
git merge origin/main
```
