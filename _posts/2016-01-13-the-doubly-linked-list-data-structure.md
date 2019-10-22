---
layout:     post
title:      "The Doubly Linked List data structure"
subtitle:   "#data-structures series"
date:       2016-01-13 22:45:18
author:     "Benoit VALLON"
header-img: "/img/2016-01-13-the-doubly-linked-list-data-structure/post-the-doubly-linked-list-data-structure.jpg"
comments:   true
categories: data-structures-in-javascript
tags:       [algorithms, data-structures, doubly-linked-list]
---

<p></p>

{% include_relative data-structures-series/about-the-series.md %}

# The Doubly Linked List data structure

## Definition

> A Doubly Linked List is a linked data structure that consists of a set of sequentially linked records called nodes. Each node contains two fields, called links, that are references to the previous and to the next node in the sequence of nodes.
**From [Wikipedia](https://en.wikipedia.org/wiki/Doubly_linked_list)**

Having two node links allow traversal in either direction but adding or removing a node in a doubly linked list requires changing more links than the same operations on a Singly Linked List.

## Complexity

Average ||||
--- | --- | --- | ---
Access|Search|Insertion|Deletion
O(n) | O(n) | O(1) | O(1)

To get a full overview of the time and space complexity of the Doubly Linked List data structure, have a look to this excellent [Big O cheat sheet](http://bigocheatsheet.com/).

## The code


{% include_relative data-structures-series/doubly-linked-list.md %}
