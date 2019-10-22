---
layout:     post
title:      "The Shellsort algorithm"
subtitle:   "#sorting-algorithms series"
date:       2016-03-16 14:51:27
author:     "Benoit VALLON"
header-img: "/img/2016-03-16-the-shellsort-algorithm/post-the-shellsort-algorithm.jpg"
comments:   true
categories: sorting-algorithms-in-javascript
tags:       [algorithms, sorting, shellsort]
---

<p></p>

{% include_relative sorting-algorithms-series/about-the-series.md %}

# The Shellsort algorithm

## Definition

> Shellsort is an in-place comparison sort which can be seen as either a generalization of sorting by exchange (bubble sort) or sorting by insertion (insertion sort). The method starts by sorting pairs of elements far apart from each other, then progressively reducing the gap between elements to be compared. Starting with far apart elements can move some out-of-place elements into position faster than a simple nearest neighbor exchange.
**From [Wikipedia](https://en.wikipedia.org/wiki/Shellsort)**

Shellsort is a generalization of insertion sort that allows the exchange of items that are far apart. It is worth noting that for a value of `gap` equals to 1, this algorithm is equal to [insertion sort](/sorting-algorithms-in-javascript/the-insertion-sort-algorithm). Have a look at the code below and you will quickly notice the similarities.

## Visualization

If you want to have a nice visualization of the algorithm, the [visualgo.net website](https://visualgo.net/en/sorting) is a nice resource. You can play with many parameters and see which part of the algorithm is doing what.

## Complexity

Time complexity |||
--- | --- | ---
Best|Average|Worst
? | ? | ?

Note that the complexity of the Shellsort algorithm depends of the sequence of number that you use as gaps and there are a lot of different possible sequences. I think that it is nice to have a look at [this table](https://en.wikipedia.org/wiki/Shellsort#Gap_sequences) to get an overview of those possible sequences and see the resulting complexity.

I didn't mention any specific complexity above because the sequence that I am using in my example (the last one of the previous table) makes calculating the complexity impossible (it is an empirically sequence of numbers unrelated to n).

Anyway, you can still have an overview of the time and space complexity of the Shellsort algorithm with this excellent [Big O cheat sheet](http://bigocheatsheet.com/). Be careful because they look wrong to me at the time of writing this post, but hopefully they will be fixed in the future.

## The code

For each sorting algorithm, we are going to look at 2 versions of the code. The first one is the final/clean version, the one that you should remember. The second one implements some counters in order to demonstrate the different time complexities depending of the inputs.

### Clean version

{% include_relative sorting-algorithms-series/shellsort.md %}

### Version with counters

{% include_relative sorting-algorithms-series/shellsort-counters.md %}
