---
layout:     post
title:      "The Bubble sort algorithm"
subtitle:   "#sorting-algorithms series"
date:       2016-03-13 15:00:28
author:     "Benoit VALLON"
header-img: "/img/2016-03-13-the-bubble-sort-algorithm/post-the-bubble-sort-algorithm.jpg"
comments:   true
categories: sorting-algorithms-in-javascript
tags:       [algorithms, sorting, bubble-sort]
---

<p></p>

{% include_relative sorting-algorithms-series/about-the-series.md %}

# The Bubble sort algorithm

## Definition

> Bubble sort is a simple sorting algorithm that repeatedly steps through the list to be sorted, compares each pair of adjacent items and swaps them if they are in the wrong order. The pass through the list is repeated until no swaps are needed, which indicates that the list is sorted.
**From [Wikipedia](https://en.wikipedia.org/wiki/Bubble_sort)**

## Visualization

If you want to have a nice visualization of the algorithm, the [visualgo.net website](https://visualgo.net/en/sorting) is a nice resource. You can play with many parameters and see which part of the algorithm is doing what.

## Complexity

Time complexity |||
--- | --- | ---
Best|Average|Worst
O(n) | O(n^2) | O(n^2)

To get a full overview of the time and space complexity of the Bubble sort algorithm, have a look to this excellent [Big O cheat sheet](http://bigocheatsheet.com/).

## The code

For each sorting algorithm, we are going to look at 2 versions of the code. The first one is the final/clean version, the one that you should remember. The second one implements some counters in order to demonstrate the different time complexities depending of the inputs.

### Clean version

{% include_relative sorting-algorithms-series/bubble-sort.md %}

### Version with counters

{% include_relative sorting-algorithms-series/bubble-sort-counters.md %}
