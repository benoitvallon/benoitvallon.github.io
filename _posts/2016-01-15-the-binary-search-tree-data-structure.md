---
layout:     post
title:      "The Binary Search Tree data structure"
subtitle:   "#data-structures series"
date:       2016-01-15 23:58:04
author:     "Benoit VALLON"
header-img: "/img/2016-01-15-the-binary-search-tree-data-structure/post-the-binary-search-tree-data-structure.jpg"
comments:   true
categories: data-structures-in-javascript
tags:       [algorithms, data-structures, binary-search-tree]
---

{% include_relative data-structures-series/about-the-series.md %}

# The Binary Search Tree data structure

## Definition

> A Binary Search Tree data structure is a rooted binary tree, whose internal nodes each store a key (and optionally, an associated value) and each have two distinguished sub-trees, commonly denoted left and right. The tree additionally satisfies the binary search tree property, which states that the key in each node must be greater than all keys stored in the left sub-tree, and smaller than all keys in right sub-tree.
**From [Wikipedia](https://en.wikipedia.org/wiki/Binary_search_tree)**

## Complexity

Average ||||
--- | --- | --- | ---
Access|Search|Insertion|Deletion
O(log(n)) | O(log(n)) | O(log(n)) | O(log(n))

To get a full overview of the time and space complexity of the Binary Search Tree data structure, have a look to this excellent [Big O cheat sheet](http://bigocheatsheet.com/).

## Interesting properties

### Height and depth

The height of a node is the length of the longest downward path to a leaf from that node. The depth of a node is the length of the path to its root.

- Height and depth of an empty tree: -1
- Height and depth of a tree with just a root node: 0
- Height of the root is the height of the tree.

### Full (perfect) and complete

A full Binary Search Tree (sometimes perfect Binary Search Tree) is a tree in which every node other than the leaves has two children. A complete Binary Search Tree is a Binary Search Tree in which every level, except possibly the last, is completely filled, and all nodes are as far left as possible.

### Edges and nodes

The height of the tree equals the number of edges between the root and a leaf. The number of levels equals the `height + 1`.

Number of nodes: `2^levels - 1` maximum nodes where `levels = height + 1` where `height = edges-between-root-and-leaf`

- 1 edge, 2 levels => `2^2 - 1 = 3` nodes N \| NN
- 2 edges, 3 levels => `2^3 - 1 = 7` nodes N \| NN \| NN NN
- 3 edges, 4 levels => `2^4 - 1 = 15` nodes N \| NN \| NN NN \| NN NN NN NN

Maximum number of nodes at i level = `2^(i - 1)` (level 0 => 1, level 1 => 2, level 2 => 4, level 3 => 8)

- if n nodes, than `number of levels = log(n + 1)`, depth still levels - 1
- if n nodes, than the `number of edges = n - 1`

## The code

{% include_relative data-structures-series/binary-search-tree.md %}
