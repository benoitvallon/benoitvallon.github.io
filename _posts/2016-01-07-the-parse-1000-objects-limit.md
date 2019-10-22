---
layout:     post
title:      "The Parse 1,000 objects limit"
subtitle:   "Get easily more than a 1,000 objects"
date:       2016-01-07 10:25:02
author:     "Benoit VALLON"
header-img: "/img/2016-01-07-the-parse-1000-objects-limit/post-the-parse-1000-objects-limit.jpg"
comments:   true
categories: tips
tags:       [database, Parse, tips]
---

# The Parse 1,000 objects limit

If you have worked with Parse recently or in the past, you must be familiar with this limit. As stated in [their documentation](https://www.parse.com/docs/js/guide#performance-limits-and-other-considerations) you can't get more than 1,000 objects per request and if you need to retrieve 1,500 objects for example you will need to use paginated queries.

> Queries can only return up to 1,000 objects in a single result set.

Furthermore, even with the pagination you won't be able to retrieve more than 10,000 objects. Hopefully this limit is high enough.

## At [Bubble](https://www.appbubble.co/#ae2)

At [Bubble](https://www.appbubble.co/#ae2) we have users having more than a 1,000 albums so we needed a way to requests their albums efficiently.

We first decided to host our code in [cloud code](https://www.parse.com/docs/cloudcode/guide) when possible. This allowed us to have a greatly simplified version of the front-end of our stack (the app). Moreover we can now update our "API queries" without having to release a new version of the app which is very convenient to move fast.


![App sreenshots](/img/2016-01-07-the-parse-1000-objects-limit/bubble-screenshot.jpg "App sreenshots")

# How to request more than 1,000 objects

You will have to use the pagination through the `skip` method. The problem is that you generally don't know how many results you will get. Is it 200 or 1,200? It seems to be a typical recursive problem. But how to do recursion with the Parse queries.

## Your application query

Let's suppose you want to get all the albums of an author.

First you need to define your Parse query. You can add all the conditions that you need, for example we will add a condition on the author name.

```js
var Album = Parse.Object.extend('Album');
var queryAlbums = new Parse.Query(Album);

queryAlbums.equalTo('author', 'Jean Van Hamme');
```

## Initiate the recursive queries

Once you have defined your query, you can now start a recursive process of queries. The process will at the end return only one promise that will return the accumulated results if the promise resolved. You also need to pass a variable to the recursive process where you will store all the queries results along the process.

```js
var allAlbums = [];

return recursiveQuery(queryAlbums, 0, allAlbums).then(function(albums) {
    // do something with the albums if needed
    return albums;
  },
  function(error) {
    return error;
  }
);
```

## In the recursion

The `recursiveQuery` function is the one in the middle of the process. It doesn't do the queries per se, but handles the pagination and build the accumulated results.

```js
function recursiveQuery(query, batchNumber, allObjects) {
  return simpleQuery(query, batchNumber).then(function(objects) {
    // concat the intermediate objects into the final array
    allObjects = allObjects.concat(objects);
    // if the objects length is 1000, it means that we are not at the end of the list
    if (objects.length === 1000) {
      batchNumber = batchNumber + 1;
      return recursiveQuery(query, batchNumber, allObjects);
    } else {
      return allObjects;
    }
  });
}
```

This function also calls a much simpler function `simpleQuery` which is the one that makes the real query. The `skip` property is defined by the argument sent by the `recursiveQuery` which manages the pagination.

```js
function simpleQuery(query, batchNumber) {
  query.limit(1000);
  query.skip(batchNumber * 1000);

  return query.find().then(
    function(objects) {
      return objects;
    },
    function(error) {
      return error;
    }
  );
}
```

# All the code

Here is all the code. As we did at [Bubble](https://www.appbubble.co/#ae2) I strongly advise you to put your code in [cloud code](https://www.parse.com/docs/cloudcode/guide) to gain in performance.

```js
function simpleQuery(query, batchNumber) {
  query.limit(1000);
  query.skip(batchNumber * 1000);

  return query.find().then(
    function(objects) {
      return objects;
    },
    function(error) {
      return error;
    }
  );
}

function recursiveQuery(query, batchNumber, allObjects) {
  return simpleQuery(query, batchNumber).then(function(objects) {
    // concat the intermediate objects into the final array
    allObjects = allObjects.concat(objects);
    // if the objects length is 1000, it means that we are not at the end of the list
    if (objects.length === 1000) {
      batchNumber = batchNumber + 1;
      return recursiveQuery(query, batchNumber, allObjects);
    } else {
      return allObjects;
    }
  });
}

function getAllAlbums(authorName) {
  var Album = Parse.Object.extend('Album');
  var queryAlbums = new Parse.Query(Album);

  queryAlbums.equalTo('author', authorName);

  var allAlbums = [];

  return recursiveQuery(queryAlbums, 0, allAlbums).then(function(albums) {
      // do something with the albums if needed
      return albums;
    },
    function(error) {
      return error;
    }
  );
}

getAllAlbums('Jean Van Hamme');
```
