---
layout:     post
title:      "The Array data structure"
subtitle:   "#data-structures series"
date:       2016-01-12 11:27:51
author:     "Benoit VALLON"
header-img: "/img/2016-01-12-the-array-data-structure/post-the-array-data-structure.jpg"
comments:   true
categories: data-structures-in-javascript
tags:       [algorithms, data-structures, array]
---

{% include_relative data-structures-series/about-the-series.md %}

# The Array data structure

## Definition

> An Array data structure, or simply an Array, is a data structure consisting of a collection of elements (values or variables), each identified by at least one array index or key. The simplest type of data structure is a linear array, also called one-dimensional array.
**From [Wikipedia](https://en.wikipedia.org/wiki/Array_data_structure)**

Arrays are among the oldest and most important data structures and are used by every program. They are also used to implement many other data structures.

## Complexity

Average ||||
--- | --- | --- | ---
Access|Search|Insertion|Deletion
O(1) | O(n) | O(n) | O(n)

To get a full overview of the time and space complexity of the Array data structure, have a look to this excellent [Big O cheat sheet](http://bigocheatsheet.com/).

## The code

{% include_relative data-structures-series/array.md %}
