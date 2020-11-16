---
id: 005-fatal-git-tree.md
title: fatal git-write-tree error building trees
tags:
  - git
  - git-write
  - git pull
author: Zoran Pandovski
meta-description: 
date: 2020-06-14 18:52:57 +0200
template: post
categories:
  - git
cover: ../images/categories/git.png
---

If you search the above error, most of the answers would be to use `git reset --hard` command. But, you should be careful with executing this command. You can lose all uncommitted changes from your working tree. So how to resolve this error?

```
fatal: git-write-tree: error building trees
Cannot save the current index state
```

This error usually happens when you have conflicts or unmerged paths. To check the unmerged paths run:

```
git status
```

This should show the following message:

```
$ git status
> # On branch add-helpers
> # You have unmerged paths.
> #   (fix conflicts and run "git commit")
> #
> # Unmerged paths:
> #   (use "git add ..." to mark resolution)
> #
> # both modified:      utilities/helpers.py
> #
> no changes added to commit (use "git add" and/or "git commit -a")
```

Open the file with conflicts and look for the conflict markers `<<<<<` and `>>>>>`. Make the changes you want to keep and then add your changes:

```git
git add utilities/helpers.py
```

Now, you will be able to commit your changes or switch to another branch.