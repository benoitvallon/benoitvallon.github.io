---
layout:     post
title:      "The Graph data structure"
subtitle:   "#data-structures series"
date:       2016-02-15 07:26:11
author:     "Benoit VALLON"
header-img: "/img/2016-02-15-the-graph-data-structure/post-the-graph-data-structure.jpg"
comments:   true
categories: data-structures-in-javascript
tags:       [algorithms, data-structures, graph]
---

<p></p>

{% include_relative data-structures-series/about-the-series.md %}

# The Graph data structure

## Definition

> A Graph data structure consists of a finite (and possibly mutable) set of vertices or nodes or points, together with a set of unordered pairs of these vertices for an undirected Graph or a set of ordered pairs for a directed Graph. These pairs are known as edges, arcs, or lines for an undirected Graph and as arrows, directed edges, directed arcs, or directed lines for a directed Graph. The vertices may be part of the Graph structure, or may be external entities represented by integer indices or references.
**From [Wikipedia](https://en.wikipedia.org/wiki/Graph_(abstract_data_type))**

A Graph data structure may also associate to each edge some edge value, such as a symbolic label or a numeric attribute (cost, capacity, length, etc.).

## Representation

There are different ways of representing a graph, each of them with its own advantages and disadvantages. Here are the main 2:

- Adjacency list: For every vertex a list of adjacent vertices is stored. This can be viewed as storing the list of edges. This data structure allows the storage of additional data on the vertices and edges.
- Adjacency matrix: Data are stored in a two-dimensional matrix, in which the rows represent source vertices and columns represent destination vertices. The data on the edges and vertices must be stored externally.

## Complexity

Adjacency list ||||
--- | --- | --- | ---
Storage|Add Vertex|Add Edge|Query
O(\|V\|+\|E\|) | O(1) | O(1) | O(\|V\|)

Adjacency matrix ||||
--- | --- | --- | ---
Storage|Add Vertex|Add Edge|Query
O(\|V\|^2) | O(\|V\|^2) | O(1) | O(1)

To get a full overview of the time and space complexity of the Graph data structure, have a look to this excellent [Big O cheat sheet](http://bigocheatsheet.com/).

## Our sample graph

The following sample graph is the one that our code sample will reproduce. It is a nice image from wikipedia on the [Graph theory](https://en.wikipedia.org/wiki/Graph_theory).

![Graph](/img/2016-02-15-the-graph-data-structure/graph-view.jpg "Graph")

## The code

The code below uses the adjacency list representation.

{% include_relative data-structures-series/graph.md %}
