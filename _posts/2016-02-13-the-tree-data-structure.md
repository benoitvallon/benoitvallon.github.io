---
layout:     post
title:      "The Tree data structure"
subtitle:   "#data-structures series"
date:       2016-02-13 23:11:19
author:     "Benoit VALLON"
header-img: "/img/2016-02-13-the-tree-data-structure/post-the-tree-data-structure.jpg"
comments:   true
categories: data-structures-in-javascript
tags:       [algorithms, data-structures, tree]
---

{% include_relative data-structures-series/about-the-series.md %}

# The Tree data structure

## Definition

> A Tree is a widely used data structure that simulates a hierarchical tree structure, with a root value and subtrees of children with a parent node. A tree data structure can be defined recursively as a collection of nodes (starting at a root node), where each node is a data structure consisting of a value, together with a list of references to nodes (the "children"), with the constraints that no reference is duplicated, and none points to the root node.
**From [Wikipedia](https://en.wikipedia.org/wiki/Tree_(data_structure))**

## Complexity

Average ||||
--- | --- | --- | ---
Access|Search|Insertion|Deletion
O(n) | O(n) | O(n) | O(n)

To get a full overview of the time and space complexity of the Tree data structure, have a look to this excellent [Big O cheat sheet](http://bigocheatsheet.com/).

## The code

{% include_relative data-structures-series/tree.md %}
