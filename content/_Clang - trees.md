---
title: _Clang - trees
author: Arthur Pieri
tags:
  - clang
  - ComputerScience
  - data-engineering
---
#clang #data-engineering #ComputerScience 

## Types of Trees
### [[Binary Search Tree]]
- Each node has at most 2 children
- The left child is less than the parent
- The right child is greater than the parent
- No duplicates
### [[AVL Tree]]
- Self-balancing binary search tree
- The height of left and right subtrees of any node differ by at most 1
- Insertion and deletion operations may cause the tree to become unbalanced
### [[Red-Black Tree]]
- Self-balancing binary search tree
- Each node is either red or black
- The root node is always black
- New nodes are always red
- No two adjacent red nodes
- Every path from a node to a null node has the same number of black nodes
### [[Balanced-Tree (B-tree)]]
- Self-balancing tree
- Each node can have more than 2 children
- Used in databases and file systems
- Each node contains a list of keys and a list of children
- Keys are sorted in ascending order
- Keys in the left child are less than the keys in the parent node
- Keys in the right child are greater than the keys in the parent node
- All leaves are at the same level
### [[B+ Tree]]
- Self-balancing tree
- Each node can have more than 2 children
- Used in databases and file systems
- Each node contains a list of keys and a list of children
- Keys are sorted in ascending order
- Keys in the left child are less than or equal to the keys in the parent node
- Keys in the right child are greater than the keys in the parent node
- All leaves are at the same level
- All keys are present in the leaf nodes
- Leaf nodes are linked together
### [[Splay Tree]]
- Self-balancing binary search tree
- Recently accessed nodes are moved closer to the root
- Used in caches and memory allocators