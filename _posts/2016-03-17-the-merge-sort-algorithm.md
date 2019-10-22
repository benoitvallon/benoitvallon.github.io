---
layout:     post
title:      "The Merge sort algorithm"
subtitle:   "#sorting-algorithms series"
date:       2016-03-17 12:07:11
author:     "Benoit VALLON"
header-img: "/img/2016-03-17-the-merge-sort-algorithm/post-the-merge-sort-algorithm.jpg"
comments:   true
categories: sorting-algorithms-in-javascript
tags:       [algorithms, sorting, merge-sort]
---

<p></p>

{% include_relative sorting-algorithms-series/about-the-series.md %}

# The Merge sort algorithm

## Definition

> Merge sort is a divide and conquer algorithm. Conceptually, a Merge sort works as follows: 1) Divide the unsorted list into n sublists, each containing 1 element (a list of 1 element is considered sorted), 2) Repeatedly merge sublists to produce new sorted sublists until there is only 1 sublist remaining. This will be the sorted list.
**From [Wikipedia](https://en.wikipedia.org/wiki/Merge_sort)**

## Visualization

If you want to have a nice visualization of the algorithm, the [visualgo.net website](https://visualgo.net/en/sorting) is a nice resource. You can play with many parameters and see which part of the algorithm is doing what.

## Complexity

Time complexity |||
--- | --- | ---
Best|Average|Worst
O(n log(n)) | O(n log(n)) | O(n log(n))

To get a full overview of the time and space complexity of the Merge sort algorithm, have a look to this excellent [Big O cheat sheet](http://bigocheatsheet.com/).

## The code

For each sorting algorithm, we are going to look at 2 versions of the code. The first one is the final/clean version, the one that you should remember. The second one implements some counters in order to demonstrate the different time complexities depending of the inputs.

### Clean version

{% include_relative sorting-algorithms-series/merge-sort.md %}

### Version with counters

{% include_relative sorting-algorithms-series/merge-sort-counters.md %}
