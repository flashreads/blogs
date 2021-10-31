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
cover: ../../images/categories/python.png
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


Code Example : 

```python:
# Binary Search Tree operations in Python


# Create a node
class Node:
    def __init__(self, key):
        self.key = key
        self.left = None
        self.right = None


# Inorder traversal
def inorder(root):
    if root is not None:
        # Traverse left
        inorder(root.left)

        # Traverse root
        print(str(root.key) + "->", end=' ')

        # Traverse right
        inorder(root.right)


# Insert a node
def insert(node, key):

    # Return a new node if the tree is empty
    if node is None:
        return Node(key)

    # Traverse to the right place and insert the node
    if key < node.key:
        node.left = insert(node.left, key)
    else:
        node.right = insert(node.right, key)

    return node


# Find the inorder successor
def minValueNode(node):
    current = node

    # Find the leftmost leaf
    while(current.left is not None):
        current = current.left

    return current


# Deleting a node
def deleteNode(root, key):

    # Return if the tree is empty
    if root is None:
        return root

    # Find the node to be deleted
    if key < root.key:
        root.left = deleteNode(root.left, key)
    elif(key > root.key):
        root.right = deleteNode(root.right, key)
    else:
        # If the node is with only one child or no child
        if root.left is None:
            temp = root.right
            root = None
            return temp

        elif root.right is None:
            temp = root.left
            root = None
            return temp

        # If the node has two children,
        # place the inorder successor in position of the node to be deleted
        temp = minValueNode(root.right)

        root.key = temp.key

        # Delete the inorder successor
        root.right = deleteNode(root.right, temp.key)

    return root


root = None
root = insert(root, 8)
root = insert(root, 3)
root = insert(root, 1)
root = insert(root, 6)
root = insert(root, 7)
root = insert(root, 10)
root = insert(root, 14)
root = insert(root, 4)

print("Inorder traversal: ", end=' ')
inorder(root)

print("\nDelete 10")
root = deleteNode(root, 10)
print("Inorder traversal: ", end=' ')
inorder(root)
```
