---
layout:     post
title:      "The Queue data structure"
subtitle:   "#data-structures series"
date:       2016-01-14 19:21:30
author:     "Benoit VALLON"
header-img: "/img/2016-01-14-the-queue-data-structure/post-the-queue-data-structure.jpg"
comments:   true
categories: data-structures-in-javascript
tags:       [algorithms, data-structures, queue]
---

{% include_relative data-structures-series/about-the-series.md %}

# The Queue data structure

## Definition

> A Queue is a particular kind of abstract data type or collection in which the entities in the collection are kept in order and the principal operations are the addition of entities to the rear terminal position, known as enqueue, and removal of entities from the front terminal position, known as dequeue. This makes the Queue a First-In-First-Out (FIFO) data structure. In a FIFO data structure, the first element added to the Queue will be the first one to be removed.
**From [Wikipedia](https://en.wikipedia.org/wiki/Queue_(abstract_data_type))**

As for the Stack data structure, a peek operation is often added to the Queue data structure. It returns the value of the front element without dequeuing it.

## Complexity

Average ||||
--- | --- | --- | ---
Access|Search|Insertion|Deletion
O(n) | O(n) | O(1) | O(n)

To get a full overview of the time and space complexity of the Queue data structure, have a look to this excellent [Big O cheat sheet](http://bigocheatsheet.com/).

## The code

{% include_relative data-structures-series/queue.md %}
