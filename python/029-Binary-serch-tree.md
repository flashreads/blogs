---
id: 029-Binary-serch-tree.md
title: What are Binary serch tree in python
tags:
  - python
  - random
author: Aryan Nath
meta-description: Why binary serch trees are important
date: 2021-10-08 15:41:42 -0700
keywords: python
template: post
categories:
  - python
cover:
---

## What is Binary search Trees?

Binary Search Tree is a node-based binary tree data structure which has the following properties:  

The left subtree of a node contains only nodes with keys lesser than the node’s key.
The right subtree of a node contains only nodes with keys greater than the node’s key.
The left and right subtree each must also be a binary search tree. 
There must be no duplicate nodes.

###Pros of a BST

* When balanced, a BST provides lightning-fast O(log(n)) insertions, deletions, and lookups.
* Binary search trees are pretty simple. An ordinary BST, unlike a balanced tree like a red-black tree, requires very little code to get running.

###Cons of a BST

* Slow for a brute-force search. If you need to iterate over each node, you might have more success with an array.
* When the tree becomes unbalanced, all fast O(log(n)) operations quickly degrade to O(n).
* Since pointers to whole objects are typically involved, a BST can require quite a bit more memory than an array, although this depends on the implementation.

There are many applications of binary search trees in real life, and one of the most common use cases is storing indexes and keys in a database. For example, when you create a primary key column in MySQL or PostgresQL, you create a binary tree where the keys are the values of the column and the nodes point to database rows. This allows the application to easily search for database rows by specifying a key, for example, to find a user record using the email primary key.
