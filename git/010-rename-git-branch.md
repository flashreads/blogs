---
id: 010-rename-git-branch.md
title: Rename a branch in Git repository
tags:
  - Git
  - Github
  - Git Branch
author: Pavle Jonoski
meta-description: Rename a branch in local and remote Git repository
date: 2022-10-22 17:40:00 +0200
keywords: Git, Github, Git Branch
template: post
categories:
  - git
image: assets/images/pipe.svg
---

# Rename a branch in local and remote Git repository

You can easily rename a local Git branch.

Assuming you are already on the checked out branch:

```bash
git branch -m <new_branch_name>
```

`-m` is shorthand for `--move`, which means to "move" (rename) the current branch to another name.

For example, let's assume we have a local Git repository and we have checked out the branch `my_branch`.
If we want to rename this branch to `my_new_branch`, we can do something like this:

```bash
$ git status
On branch my_branch
nothing to commit, working tree clean

$ git branch -m my_new_branch
$ git status
On branch my_new_branch
nothing to commit, working tree clean
```

## Renaming a remote branch on Github

If your branch is set up to track a branch in the remote repository, you'll have to push the name update as well.

First you need to delete the upstream branch:

```bash
git push origin :<old-branch>
```

then, push and set the current branch to track the upstream branch:

```bash
git push --set-upstream origin <new_branch_name>
```

A full example:

```bash
$ git branch -m my_new_branch  # rename current branch to 'my_new_branch'
$ git push origin :my_branch   # 'my_branch' was the old name of the branch
$ git push --set-upstream origin my_new_branch  # push the branch under a new name and set
                                                # the local branch to track the upstream branch.
```
