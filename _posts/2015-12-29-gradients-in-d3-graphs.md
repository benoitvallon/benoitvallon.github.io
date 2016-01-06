---
layout:     post
title:      "Gradients in D3 Graphs"
subtitle:   "Make nice gradients for your D3 curves and shapes"
date:       2015-12-29 12:45:57
author:     "Benoit VALLON"
header-img: "/img/2015-12-29-gradients-in-d3-graphs/post-gradients-in-d3-graphs.jpg"
comments:   true
categories: tips
tags:       [D3, gradient, tips]
---

# Gradient in D3 Graphs

When I worked on my [Air Colors app](http://www.air-colors.io/) a few months ago I had to implement some D3 graphs with the particularity of having gradients.

They look like this. They had curves but also areas and some of them has to be with transparency.

![App sreenshots](/img/2015-12-29-gradients-in-d3-graphs/app-screenshots.jpg "App sreenshots")

# Gradients and SVG

Applying a gradient to an element of a D3 graph is basically equivalent to apply a gradient to any SVG element. Therefore you just need to define a gradient tag in your SVG and reference this gradient in the styling of your SVG element.

The following example if from the [MDN](https://developer.mozilla.org/fr/docs/Web/SVG/Element/linearGradient)

```html
<svg width="120" height="120"  viewBox="0 0 120 120"
     xmlns="http://www.w3.org/2000/svg" version="1.1"
     xmlns:xlink="http://www.w3.org/1999/xlink" >
  <defs>
    <linearGradient id="MyGradient">
      <stop offset="5%"  stop-color="green"/>
      <stop offset="95%" stop-color="gold"/>
      </linearGradient>
  </defs>
  <rect fill="url(#MyGradient)" x="10" y="10" width="100" height="100"/>
</svg>
```

# [Air Colors](http://www.air-colors.io/) specificity

The previous example is pretty simple because the offsets which define the gradient limits are fixed and you know the scale of your graph. What if you want something dynamic as it is in [Air Colors](http://www.air-colors.io/).

What I mean by dynamic is that your scale is unknown. For example your Y scale can go from 0 to 500 and the different limits for your color transitions should be 100, 200 and so on. It wouldn't be a problem if you always display your graph with the scale from 0 to 500, then your offsets would be something like 20%, 40% and so on.

But how would you do if your graph can go from 0 to 500 but most of the time the interesting part of the graph is between, let's say, 0 to 300. Then your offsets must be different, probably around 33%, 66% and 100%.

## Define a reference for your gradients limits

To handle this I first define an array of reference for my gradient limits. I defined 2 colors here, one for the lines and the other for the colored areas. As you can see I also defined an opacity to apply on the colored areas, that is how you can still see the map of the city in the background.

```js
...
AQI.getColorsAndIndexes = function() {
  return [
    {indexLte: 300, backgroundColor: '#e8c1f3', borderColor: '#d182e8', opacity: 0.8},
    {indexLte: 150, backgroundColor: '#f76454', borderColor: '#f34b38', opacity: 0.7},
    {indexLte: 100, backgroundColor: '#f7b854', borderColor: '#f4ac39', opacity: 0.65},
    {indexLte: 50, backgroundColor: '#f7e654', borderColor: '#f1de37', opacity: 0.6},
    {indexLte: 20, backgroundColor: '#a7ea6b', borderColor: '#9ddd65', opacity: 0.55},
    {indexLte: 0, backgroundColor: '#5dee52', borderColor: '#00e400', opacity: 0.5},
  ];
};
...  
```

## Calculate your offsets dynamically according to your reference

This is the hardest part because you want to be sure that your offset will be correctly calculated if you want to see your gradients. Moreover sometimes the color you choose for your gradients will make difficult to really see the transition in the gradients and you can be fooled if you simply adjust your offsets visually.

In the next code sample I am calculated the new offsets based on the max value of the scale of my graph.

```js
var colorsAndIndexes = AQI.getColorsAndIndexes();
var max = d3.max(data, function(d) { return getY(d); });

for (var color in colorsAndIndexes) {
  if (colorsAndIndexes.hasOwnProperty(color)) {
    if(colorsAndIndexes[color].offset === undefined) {
      if(!isNaN((1 - colorsAndIndexes[color].indexLte / max) * 100) &&
          isFinite((1 - colorsAndIndexes[color].indexLte / max) * 100) &&
          (1 - colorsAndIndexes[color].indexLte / max) * 100 !== NaN) {
        colorsAndIndexes[color].offset = (1 - colorsAndIndexes[color].indexLte / max) * 100;
      } else {
        colorsAndIndexes[color].offset = 0;
      }
    }
  }
}

/*=> colorsAndIndexes equals:
[{
  backgroundColor: "#e8c1f3"
  borderColor: "#d182e8"
  indexLte: 300
  offset: -347.7611940298507
  opacity: 0.8
}, {
  backgroundColor: "#f76454"
  borderColor: "#f34b38"
  indexLte: 150
  offset: -123.88059701492536
  opacity: 0.7
}, {
  backgroundColor: "#f7b854"
  borderColor: "#f4ac39"
  indexLte: 100
  offset: -49.25373134328359
  opacity: 0.65
}, {
  backgroundColor: "#f7e654"
  borderColor: "#f1de37"
  indexLte: 50
  offset: 25.373134328358205
  opacity: 0.6
}, {
  backgroundColor: "#a7ea6b"
  borderColor: "#9ddd65"
  indexLte: 20
  offset: 70.1492537313433
  opacity: 0.55
}, {
  backgroundColor: "#5dee52"
  borderColor: "#00e400"
  indexLte: 0
  offset: 100
  opacity: 0.5
}]
*/
```

## Add your gradient definition in your SVG

Once you have calculated your gradient offsets and have your gradient definition ready, you can save it in your SVG using the D3 API. Nothing really new here, storing your gradient definition in the SVG `defs` tag is a good practice.

```js
svg.append('defs')
    .append('linearGradient')
    .attr('gradientUnits', 'userSpaceOnUse').attr('id', 'gradient-area')
    .attr('x1', 0).attr('y1', 0).attr('x2', 0).attr('y2', y(0))
    .selectAll('stop')
      .data(colorsAndIndexes) // <= your new offsets array
    .enter().append('stop')
      .attr('offset', function(d) { return d.offset + '%'; })
      .attr('style', function(d) { return 'stop-color:' + d.backgroundColor + ';stop-opacity:' + d.opacity; });
```

## Style your SVG Element

Finally, the last part is to style your SVG element with the gradient definition that you made.

``` js
svg.append('path')
    .datum(data)
    .attr('class', 'area')
    .attr('style', 'fill: url(#gradient-area);')
    .attr('d', areaStart)
    .transition()
      .duration(animationDuration)
      .attr('d', area);
```

# Bonus

[This post from mbostock’s blocks](http://bl.ocks.org/mbostock/3969722) shows all the code to use gradients in D3 but it is simpler than this post because it uses a fixed scale.

Tweet me if you think that you know which city is illustrated as background of the main image of the post.
