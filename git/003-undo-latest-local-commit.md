---
id: 003-undo-latest-local-commit.md
title: How to undo the latest local commit in Git repository
tags:
  - git
  - revert
  - git-revert
  - rest
  - git-reset
  - git-rebase
author: Pavle Jonoski
meta-description: What to do when you want to undo the latest commit in your repository? You have multiple options...
date: 2020-05-19 22:44:45 +0200
keywords: git, revert, git-revert, rest, git-reset, git-rebase
template: post
categories:
  - git
cover: ../../images/categories/git.png
---

# Undo the latest local commit in Git

So we've committed some changes by mistake and we want to revert it back. No worries, Git is here to help!

Depending on what we need, we can do one of the following:

## Undo all changes in the last commit

To undo all changes made in the last commit, and go back to an earlier commit, we
can use `git revert`.

Let's say we have some repository, and we committed something by mistake:

```bash
$ git log --oneline 
cba9069 (HEAD -> master) Oops, this change is a mistake  <-- We want to revert this commit
5b7794b Some stable changes
e57b197 Adds some content
187ea9d Initial commit

```

Then, to revert the latest commit, we can use `git revert <commit sha>`:

```bash
git revert cba9069
```

This will pop up our favorite editor to enter the revert commit message and will create
a new commit, which reverts **all** changes in the given commit.

After the command is complete, the repository history will look like this:

```bash
$ git log --oneline 
0ed5618 (HEAD -> master) Revert "Oops, this change is a mistake"   <-- this reverts all changes from cba9069
cba9069 Oops, this change is a mistake
5b7794b Some stable changes   <-- The final state of the repository will be the same as in this commit
e57b197 Adds some content
187ea9d Initial commit
```

As you can see, there is an additional commit that reverted our changes and the final state of the repository is
the same as the state it had in the previous commit (the commit before the one we wanted to revert).

This is useful when we want to keep the repository history and it is the recommended way of doing things. The upside
is that we haven't lost any data, even if we change our mind later, we can always revert again or see the changes in the
reverted commit - it's all there in the history.

## Reset the changes, modify and commit again

Sometimes we don't want to revert everything, but instead we need to make just a couple of changes and commit again.

In these situations we can use `git reset --soft <commit-ref>`:

Given the same state of the repository:

```
$ git log --oneline 
cba9069 (HEAD -> master) Oops, this change is a mistake  <-- We want to make some changes here again and commit
5b7794b Some stable changes
e57b197 Adds some content
187ea9d Initial commit

```

Then we can do:

```bash
git reset --soft HEAD^
```

This makes a soft reset to the commit that is parent of the current HEAD (the current HEAD is what we want to change).
Soft reset means that Git will undo the changes of the commit in the following way:

 * The HEAD of the repository will now point to `5b7794b Some stable changes` (HEAD^ - one up from current HEAD)
 * The changes introduced in the faulty commit are not lost, but are staged in the repository

This gives us the opportunity to redo the changes and commit again.
Doing a `git status` to see the changes we see something like this:

```bash
$ git status 
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   README.md

```

And the history log:
```bash
$ git log --oneline 
5b7794b (HEAD -> master) Some stable changes
e57b197 Adds some content
187ea9d Initial commit

```

This is exactly what we wanted. After doing the changes we can commit:

```bash
$ git commit -m "Fixed the commit"

$ git log --oneline
55293e6 (HEAD -> master) Fixed the commit
5b7794b Some stable changes
e57b197 Adds some content
187ea9d Initial commit

```

## Getting rid of the commit completely

Sometimes we want to get rid of the commit completely. Maybe we have committed some sensitive data by mistake (like 
an access key or password), and we want no trace of it in the history. In those cases, we can rebase the branch and 
drop the commits we don't want.

Again starting with the same repository, we can rebase on the parent commit of the good commit (going 2 commits back, 
because we cannot drop a commit if there is just one commit in the rebase list):

```bash
$ git log --oneline 
cba9069 (HEAD -> master) Oops, this change is a mistake  <-- We want this gone
5b7794b Some stable changes
e57b197 Adds some content <-- we pass this commit to the rebase command, so we have 2 commits in the list
187ea9d Initial commit

```

Rebase:
```bash
git rebase -i e57b197
```

In the rebase editor:

```
pick 5b7794b Some stable changes  <-- we want to keep this
drop cba9069 Oops, this change is a mistake <-- but we want to drop this
```

Save, and commit.

The final state of the repository:

```bash
$ git log --oneline 
5b7794b (HEAD -> master) Some stable changes
e57b197 Adds some content
187ea9d Initial commit
```

And there are no changes staged for commit:

```
$ git status 
On branch master
nothing to commit, working tree clean
```

**Important Note:** This will completely remove any trace of the commit, so once done, it is very hard to get 
those changes back if we change our mind later on. We should use this approach only if we are **certain** that we
want that commit completely gone.

## Final notes

When using approaches 2 and 3 (using `reset` and `rebase`), we're making changes in the repository graph itself. While
locally this is absolutely fine, there might be a problem when we're having a remote repository.
When the commit we want to revert is on the remote repository as well, then the two repositories will have different
graphs and we cannot `push` our changes in a straight forward manner without Git complaining that the branches 
have diverged.

Approach 1 however, when using `git revert`, adds an additional commit, just like a regular commit, which then can
be easily pushed to the remote repository.
