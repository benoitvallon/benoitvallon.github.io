---
layout:     post
title:      "The Selection sort algorithm"
subtitle:   "#sorting-algorithms series"
date:       2016-03-14 12:22:59
author:     "Benoit VALLON"
header-img: "/img/2016-03-14-the-selection-sort-algorithm/post-the-selection-sort-algorithm.jpg"
comments:   true
categories: sorting-algorithms-in-javascript
tags:       [algorithms, sorting, selection-sort]
---

{% include_relative sorting-algorithms-series/about-the-series.md %}

# The Selection sort algorithm

## Definition

> The Selection sort algorithm divides the input list into two parts: the sublist of items already sorted and the sublist of items remaining to be sorted that occupy the rest of the list. Initially, the sorted sublist is empty and the unsorted sublist is the entire input list. The algorithm proceeds by finding the smallest element in the unsorted sublist, exchanging it with the leftmost unsorted element, and moving the sublist boundaries one element to the right.
**From [Wikipedia](https://en.wikipedia.org/wiki/Selection_sort)**

## Visualization

If you want to have a nice visualization of the algorithm, the [visualgo.net website](http://visualgo.net/sorting.html) is a nice resource. You can play with many parameters and see which part of the algorithm is doing what.

## Complexity

Time complexity |||
--- | --- | ---
Best|Average|Worst
O(n^2) | O(n^2) | O(n^2)

To get a full overview of the time and space complexity of the Selection sort algorithm, have a look to this excellent [Big O cheat sheet](http://bigocheatsheet.com/).

## The code

For each sorting algorithm, we are going to look at 2 versions of the code. The first one is the final/clean version, the one that you should remember. The second one implements some counters in order to demonstrate the different time complexities depending of the inputs.

### Clean version

{% include_relative sorting-algorithms-series/selection-sort.md %}

### Version with counters

{% include_relative sorting-algorithms-series/selection-sort-counters.md %}
