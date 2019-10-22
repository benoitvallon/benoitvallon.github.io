---
layout:     post
title:      "The Singly Linked List data structure"
subtitle:   "#data-structures series"
date:       2016-01-13 10:38:41
author:     "Benoit VALLON"
header-img: "/img/2016-01-13-the-singly-linked-list-data-structure/post-the-singly-linked-list-data-structure.jpg"
comments:   true
categories: data-structures-in-javascript
tags:       [algorithms, data-structures, singly-linked-list]
---

<p></p>

{% include_relative data-structures-series/about-the-series.md %}

# The Singly Linked List data structure

## Definition

> A Singly Linked List is a linear collection of data elements, called nodes pointing to the next node by means of pointer. It is a data structure consisting of a group of nodes which together represent a sequence. Under the simplest form, each node is composed of data and a reference (in other words, a link) to the next node in the sequence.
**From [Wikipedia](https://en.wikipedia.org/wiki/Linked_list)**

Linked Lists are among the simplest and most common data structures because it allows for efficient insertion or removal of elements from any position in the sequence.

## Complexity

Average ||||
--- | --- | --- | ---
Access|Search|Insertion|Deletion
O(n) | O(n) | O(1) | O(1)

To get a full overview of the time and space complexity of the Singly Linked List data structure, have a look to this excellent [Big O cheat sheet](http://bigocheatsheet.com/).

## The code

{% include_relative data-structures-series/singly-linked-list.md %}
