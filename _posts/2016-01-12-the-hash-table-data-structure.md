---
layout:     post
title:      "The Hash Table data structure"
subtitle:   "#data-structures series"
date:       2016-01-12 21:11:19
author:     "Benoit VALLON"
header-img: "/img/2016-01-12-the-hash-table-data-structure/post-the-hash-table-data-structure.jpg"
comments:   true
categories: data-structures-in-javascript
tags:       [algorithms, data-structures, hash-table]
---

{% include_relative data-structures-series/about-the-series.md %}

# The Hash Table data structure

## Definition

> A Hash Table (Hash Map) is a data structure used to implement an associative array, a structure that can map keys to values. A Hash Table uses a hash function to compute an index into an array of buckets or slots, from which the desired value can be found.
**From [Wikipedia](https://en.wikipedia.org/wiki/Hash_table)**

Hash Tables are considered the more efficient data structure for lookup and for this reason, they are widely used.

## Complexity

Average ||||
--- | --- | --- | ---
Access|Search|Insertion|Deletion
- | O(1) | O(1) | O(1)

To get a full overview of the time and space complexity of the Hash Table data structure, have a look to this excellent [Big O cheat sheet](http://bigocheatsheet.com/).

## The code

Because my `calculateHash` function is overly simple (mod of the key length) I need to be sure that I am able to save more than one value for every hash. As a consequence I am storing another object for every hash in my Hash Table.

A better example would have had a `calculateHash` function that returns only one possible hash for every key. I could have done that with a simple JavaScript `Object` (the hash being the same as the key) but the specificity of the Hash Table data structure is to have this special `calculateHash` function.

{% include_relative data-structures-series/hash-table.md %}
