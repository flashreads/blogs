---
id: 008-git-basic-commands.md
title: Most Used Commands of Git
tags: 
  - git,
  - git cheat sheet,
  - git-commands,
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

to check your Git configuration:      git config -l
to setup your Git username:     git config --global user.name "name"
to setup your Git user email:    git config --global user.email "signups@fabiopacifici.com"
to cache your login credentials in Git:   git config --global credential.helper cache
to initialize a Git repo:    git init
to add a file to the staging area in Git:    git add filename_here
to add all files in the staging area in Git:   git add .
to add only certain files to the staging area in Git:   git add fil*
to check a repository's status in Git:  git status
to commit changes in the editor in Git:  git commit
to commit changes with a message in Git:  git commit -m "your commit message here"
to commit changes (and skip the staging area) in Git:  git commit -a -m"your commit message here"
to see your commit history in Git:   git log
to see your commit history including changes in Git:  git log -p
to see a specific commit in Git:   git show commit-id
to see log stats in Git:  git log --stat
to rename files in Git:   git mv oldfile newfile
to revert staged changes in Git:   git reset HEAD filename
                                   git reset HEAD -p
to create a new branch in Git:   git branch branch_name
to switch to a newly created branch in Git:    git checkout branch_name
to list branches in Git:   git branch
to create a branch in Git and switch to it immediately:  git checkout -b branch_name
to delete a branch in Git:  git branch -d branch_name
to merge two branches in Git:  git merge branch_name
to add a remote repository in Git:   git add remote https://repo_here
to see remote URLs in Git:   git remote -v
to push changes to a remote repo in Git:   git push
to pull changes from a remote repo in Git: git pull
to merge a remote repo with your local repo in Git:  git merge origin/main




