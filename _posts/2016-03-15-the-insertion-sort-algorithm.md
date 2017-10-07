---
layout:     post
title:      "The Insertion sort algorithm"
subtitle:   "#sorting-algorithms series"
date:       2016-03-15 12:07:11
author:     "Benoit VALLON"
header-img: "/img/2016-03-15-the-insertion-sort-algorithm/post-the-insertion-sort-algorithm.jpg"
comments:   true
categories: sorting-algorithms-in-javascript
tags:       [algorithms, sorting, insertion-sort]
---

{% include_relative sorting-algorithms-series/about-the-series.md %}

# The Insertion sort algorithm

## Definition

> Insertion sort algorithm iterates, consuming one input element each repetition, and growing a sorted output list. Each iteration removes one element from the input data, finds the location it belongs within the sorted list, and inserts it there. It repeats until no input elements remain.
**From [Wikipedia](https://en.wikipedia.org/wiki/Insertion_sort)**

This algorithm is often compared to how as human we would sort a card game for example.

## Visualization

If you want to have a nice visualization of the algorithm, the [visualgo.net website](https://visualgo.net/en/sorting) is a nice resource. You can play with many parameters and see which part of the algorithm is doing what.

## Complexity

Time complexity |||
--- | --- | ---
Best|Average|Worst
O(n) | O(n^2) | O(n^2)

To get a full overview of the time and space complexity of the Insertion sort algorithm, have a look to this excellent [Big O cheat sheet](http://bigocheatsheet.com/).

## The code

For each sorting algorithm, we are going to look at 2 versions of the code. The first one is the final/clean version, the one that you should remember. The second one implements some counters in order to demonstrate the different time complexities depending of the inputs.

### Clean version

{% include_relative sorting-algorithms-series/insertion-sort.md %}

### Version with counters

{% include_relative sorting-algorithms-series/insertion-sort-counters.md %}
