---
layout:     post
title:      "The Set data structure"
subtitle:   "#data-structures series"
date:       2016-02-13 22:55:53
author:     "Benoit VALLON"
header-img: "/img/2016-02-13-the-set-data-structure/post-the-set-data-structure.jpg"
comments:   true
categories: data-structures-in-javascript
tags:       [algorithms, data-structures, set]
---

{% include_relative data-structures-series/about-the-series.md %}

# The Set data structure

## Definition

> A Set is an abstract data type that can store certain values, without any particular order, and no repeated values. It is a computer implementation of the mathematical concept of a finite Set.
**From [Wikipedia](https://en.wikipedia.org/wiki/Set_(abstract_data_type))**

The Set data structure is usually used to test whether elements belong to set of values. Rather then only containing elements, Sets are more used to perform operations on multiple values at once with methods such as `union`, `intersect`, etc...

## Complexity

Average ||||
--- | --- | --- | ---
Access|Search|Insertion|Deletion
- | O(n) | O(n) | O(n)

To get a full overview of the time and space complexity of the Set data structure, have a look to this excellent [Big O cheat sheet](http://bigocheatsheet.com/).

## The code

{% include_relative data-structures-series/set.md %}
