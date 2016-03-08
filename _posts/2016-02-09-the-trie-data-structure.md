---
layout:     post
title:      "The Trie data structure"
subtitle:   "#data-structures series"
date:       2016-02-09 08:48:14
author:     "Benoit VALLON"
header-img: "/img/2016-02-09-the-trie-data-structure/post-the-trie-data-structure.jpg"
comments:   true
categories: data-structures-in-javascript
tags:       [algorithms, data-structures, trie]
---

{% include_relative data-structures-series/about-the-series.md %}

# The Trie data structure

## Definition

> A trie, also called digital tree and sometimes radix tree or prefix tree (as they can be searched by prefixes), is an ordered tree data structure that is used to store a dynamic set or associative array where the keys are usually strings. Unlike a binary search tree, no node in the tree stores the key associated with that node; instead, its position in the tree defines the key with which it is associated. All the descendants of a node have a common prefix of the string associated with that node, and the root is associated with the empty string. Values are not necessarily associated with every node. Rather, values tend only to be associated with leaves, and with some inner nodes that correspond to keys of interest.
**From [Wikipedia](https://en.wikipedia.org/wiki/Trie)**

## Complexity

Average ||||
--- | --- | --- | ---
Access|Search|Insertion|Deletion
O(k) | O(k) | O(k) | O(k)

where k is the word length.

To get a full overview of the time and space complexity of the Trie data structure, have a look to this excellent [Big O cheat sheet](http://bigocheatsheet.com/).

## The code

{% include_relative data-structures-series/trie.md %}
