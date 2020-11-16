---
id: 001-delete-remote-branch.md
title: Git delete a branch remotely
tags:
  - git
  - delete-branch
  - repository
  - command-line
  - github
  - github.com
author: Pavle Jonoski
meta-description: See how to delete a branch in the local and remote git repository.
date: 2020-05-12 21:53:39 +0200
template: post
categories:
  - git
cover: ../images/categories/git.png
---

# Git delete a branch from the local and remote repository

While working with Git repositories, very often you will create and need to delete
a lot of branches. Some branches will be merged into the master branch and some are
no longer necessary. In either case, at some point they need to be deleted. We want
to keep the repository clean and neat after all.

Deleting a local branch in a Git repository is quite straight forward. You can use
either of these commands to do it:

```bash
git branch -d <branch_name>
git branch -D <branch_name>
```

To delete a branch in the remote repository, you can do something very similar:

```bash
git push -d <remote> <branch_name>

# <remote> is the remote name, very often 'origin'

git push -d origin <branch_name>
```

## The difference between `-d` and `-D`

Both `-d` and `-D` are aliases:
 * `-d` is an alias for `--delete`. This deletes a branch **only** if the branch
 has already been fully merged in its upstream branch. This is very useful when
 using [git workflows](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows),
 to prevent unintentional mistakes of deleting a branch that is intended to be merged.
 Once merged, however, the branch can be safely deleted.
 * `-D` is shortcut for `--delete` `--force`. This deletes the branch regardless
 of the merge state of the branch. This is useful for deleting branches that are
 not expected to be merged.

 ## Deleting remote branch on Github repository

 Very often you need to remove a branch on a remote repository on [Github](https://github.com/).

 The regular process of creating a [Pull Request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests),
 once the branch has been merged, offers an action to delete the branch via the web
 interface:

 ![Safely Delete Branch](images/pr-merged-delete-branch.png)

 In the branch that should be deleted was not merged via *Pull Request*, then you can 
 remove it from the command line by pushing to the remote repository:

 ```bash
 git push -d origin <branch_name>
 ```

