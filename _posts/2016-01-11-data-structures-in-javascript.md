---
layout:     post
title:      "Data structures in JavaScript"
subtitle:   "#data-structures series"
date:       2016-01-11 09:14:06
author:     "Benoit VALLON"
header-img: "/img/2016-01-11-data-structures-in-javascript/post-data-structures-in-javascript.jpg"
comments:   true
categories: data-structures-in-javascript
tags:       [algorithms, data-structures]
---

{% include_relative data-structures-series/about-the-series.md %}

# The data structures in the series

- [x] [Array](/data-structures-in-javascript/the-array-data-structure)
- [x] [Hash Table](/data-structures-in-javascript/the-hash-table-data-structure)
- [x] [Set](/data-structures-in-javascript/the-set-data-structure)
- [x] [Singly Linked List](/data-structures-in-javascript/the-singly-linked-list-data-structure)
- [x] [Doubly Linked List](/data-structures-in-javascript/the-doubly-linked-list-data-structure)
- [x] [Stack](/data-structures-in-javascript/the-stack-data-structure)
- [x] [Queue](/data-structures-in-javascript/the-queue-data-structure)
- [x] [Tree](/data-structures-in-javascript/the-tree-data-structure)
- [x] [Binary Search Tree](/data-structures-in-javascript/the-binary-search-tree-data-structure)
- [x] [Trie](/data-structures-in-javascript/the-trie-data-structure)
- [x] [Graph](/data-structures-in-javascript/the-graph-data-structure)

# What is a data structure?

Instead of trying to re-explain what a data structure is, I prefer to leave you with the perfect description [wikipedia](https://en.wikipedia.org/wiki/Data_structure) makes of it.

> In computer science, a data structure is a particular way of organizing data in a computer so that it can be used efficiently.
**From [Wikipedia](https://en.wikipedia.org/wiki/Data_structure)**

"used efficiently" here means that according to your needs. You may need for example an organizing structure that allows very fast lookup or it could be very fast insertion or any thing related to your application.

The key thing to remember is that each data structure has it own advantages and disadvantages. There isn't any one of them that would beat all of the others, that's the reason why it is important to know them all.

# The complexity

If you hear about data structures, you will for sure hear about their complexity. As said before every data structure has its own advantages and disadvantages, their complexity can be seen as a way of expressing their own advantages and disadvantages easily according to a specific problem.

The complexity is expressed on 2 axes, the space and the time.

## The space

The space complexity represents the memory consumption of a data structure. As for most of the things in life, you can't have it all, so it is with the data structures. You will generally need to trade some time for space or the other way around.

## The time

The time complexity for a data structure is in general more diverse than its space complexity.

### Several operations

In contrary to algorithms, when you look at the time complexity for data structures you need to express it for several operations that you can do with data structures. It can be adding elements, deleting elements, accessing an element or even searching for an element.

### Dependent on data

Something that data structure and algorithms have in common when talking about time complexity is that they are both dealing with data. When you deal with data you become dependent on them and as a result the time complexity is also dependent of the data that you received. To solve this problem we talk about 3 different time complexity.

- The best-case complexity: when the data looks the best
- The worst-case complexity: when the data looks the worst
- The average-case complexity: when the data looks average

## The big O notation

The complexity is usually expressed with the [Big O notation](https://en.wikipedia.org/wiki/Big_O_notation). The wikipedia page about this subject is pretty complex but you can find here a good summary of the [different complexity for the most famous data structure and sorting algorithms](http://bigocheatsheet.com/).

![Big O notation cheat sheets](/img/2016-01-11-data-structures-in-javascript/big-o.png "Big O notation cheat sheets")
![Big O notation cheat sheets](/img/2016-01-11-data-structures-in-javascript/big-o-complexity.png "Big O notation cheat sheets")
