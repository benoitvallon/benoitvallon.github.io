---
layout:     post
title:      "The Stack data structure"
subtitle:   "#data-structures series"
date:       2016-01-14 09:16:37
author:     "Benoit VALLON"
header-img: "/img/2016-01-14-the-stack-data-structure/post-the-stack-data-structure.jpg"
comments:   true
categories: data-structures-in-javascript
tags:       [algorithms, data-structures, stack]
---

{% include_relative data-structures-series/about-the-series.md %}

# The Stack data structure

## Definition

> A Stack is an abstract data type that serves as a collection of elements, with two principal operations: push, which adds an element to the collection, and pop, which removes the most recently added element that was not yet removed. The order in which elements come off a Stack gives rise to its alternative name, LIFO (for last in, first out).
**From [Wikipedia](https://en.wikipedia.org/wiki/Stack_(abstract_data_type))**

A Stack often has a third method peek which allows to check the last pushed element without popping it.

## Complexity

Average ||||
--- | --- | --- | ---
Access|Search|Insertion|Deletion
O(n) | O(n) | O(1) | O(1)

To get a full overview of the time and space complexity of the Stack data structure, have a look to this excellent [Big O cheat sheet](http://bigocheatsheet.com/).

## The code

{% include_relative data-structures-series/stack.md %}
