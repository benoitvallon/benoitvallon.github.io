---
layout:     post
title:      "The Quicksort algorithm"
subtitle:   "#sorting-algorithms series"
date:       2016-03-18 14:00:03
author:     "Benoit VALLON"
header-img: "/img/2016-03-18-the-quicksort-algorithm/post-the-quicksort-algorithm.jpg"
comments:   true
categories: sorting-algorithms-in-javascript
tags:       [algorithms, sorting, quicksort]
---

<p></p>

{% include_relative sorting-algorithms-series/about-the-series.md %}

# The Quicksort algorithm

## Definition

> Quicksort is a divide and conquer algorithm. Quicksort first divides a large array into two smaller sub-arrays: the low elements and the high elements. Quicksort can then recursively sort the sub-arrays.
**From [Wikipedia](https://en.wikipedia.org/wiki/Quicksort)**

## Visualization

If you want to have a nice visualization of the algorithm, the [visualgo.net website](https://visualgo.net/en/sorting) is a nice resource. You can play with many parameters and see which part of the algorithm is doing what.

## Complexity

Time complexity |||
--- | --- | ---
Best|Average|Worst
O(n log(n)) | O(n log(n)) | O(n^2)

To get a full overview of the time and space complexity of the Merge sort algorithm, have a look to this excellent [Big O cheat sheet](http://bigocheatsheet.com/).

## The code

For each sorting algorithm, we are going to look at 2 versions of the code. The first one is the final/clean version, the one that you should remember. The second one implements some counters in order to demonstrate the different time complexities depending of the inputs.

### Clean version

{% include_relative sorting-algorithms-series/quicksort.md %}

### Version with counters

{% include_relative sorting-algorithms-series/quicksort-counters.md %}
