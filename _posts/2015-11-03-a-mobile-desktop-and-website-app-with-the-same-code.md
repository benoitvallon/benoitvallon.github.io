---
layout:     post
title:      "A mobile, desktop and website app with the same code"
subtitle:   "React-native, NW and React all together"
date:       2015-11-03 10:18:23
author:     "Benoit VALLON"
header-img: "/img/2015-11-03-a-mobile-desktop-and-website-app-with-the-same-code/post-a-mobile-desktop-and-website-app-with-the-same-code.jpg"
comments:   true
categories: projects
tags:       [react, react-native, nw, es6]
---

# React-native, NW and React, all in one

A few months ago after react-native was released I started to wonder how it would be possible to do a mobile app, desktop app and website app with the same code base. I knew it was possible but I wanted to explore how to do it and what would be the final volume of reused code. So I created the project [react-native-nw-react-calculator](https://github.com/benoitvallon/react-native-nw-react-calculator).

This project shows how the source code can be architectured to run on multiple devices. As of now, it is able to run as:

- an iOS app (based on [react-native](https://facebook.github.io/react-native))
- a desktop app (based on [NW](http://nwjs.io))
- a website app in any browser (based on [react](https://facebook.github.io/react))

It is a beautiful calculator with the previous formulae feature based on the design of Robert O'Dowd who kindly authorized me the reuse it. The original design made by Robert was part of his project called "Simplifycation" visible [here](https://dribbble.com/shots/1973851-Simplifycation).

# Like a production project

I wanted for this project to use all the tools that I would have used in a production project, so it is based on the [flux](https://facebook.github.io/flux) architecture and uses tools like [grunt](http://gruntjs.com) and [webpack](https://webpack.github.io) to create the builds and for the hot reloading feature.

# In the code

## 2 main builds

Although we are going to run on 3 devices, we only need to create 2 builds. Both entry files for those builds are at the root of the `src` directory.

- `index.ios.js` is the entry file for the iOS app build
- `index.js` is the entry file for the website app and desktop app build

The second build for the website app and desktop app is the same because it is possible to reuse the exact same code in both environment.

## Flux architecture actions/stores

All the [flux](https://facebook.github.io/flux) architecture is share at 100% to all the different builds. This means that all the logic and data management code is done once and reuse everywhere.

This allows us to have an easy tests suite as well and to ensure that our code is working properly on all the devices.

## Components

Here comes the real interest of the project. Finding how the components can be structured to share most of their logic but still allowing for some specificity for each device was not so easy.

Having inheritance for the shared logic and only redefine what is specific to every device sounds the right solution but how to include only the code that we want for each build. It could have been done with webpack and its variables evaluated during the build but thanks to [@cjbprime] (https://twitter.com/cjbprime) I managed to do it based on the file extensions.

At the end, every component has a main `Class` which inherits a base `Class` containing all the logic. Then, the main component import a different Render function which is selected during the build. The file extension `.ios.js` or `.js` is used by the different build tools to import only the right file.

Finally, every component is defined with 4 files. If we look at the screen component for example, here is its structure.

```
Screen.js
ScreenBase.js
ScreenRender.ios.js (used by the iOS build)
ScreenRender.js  (used by the website and desktop build)
```

And here is the main `Class` file which composes the other files.

```js
'use strict';

import Base from './ScreenBase';
import Render from './ScreenRender';

export default class Screen extends Base {
  constructor (props) {
    super(props);
  }

  render () {
    return Render.call(this, this.props, this.state);
  }
}
```

# All of them in action

Enough text, let's have a some images.

## Mobile App

![Mobile App](/img/2015-11-03-a-mobile-desktop-and-website-app-with-the-same-code/mobile-app.png "Mobile App")

## Desktop App

![Desktop App](/img/2015-11-03-a-mobile-desktop-and-website-app-with-the-same-code/desktop-app.png "Desktop App")

## Website App

![Website App](/img/2015-11-03-a-mobile-desktop-and-website-app-with-the-same-code/website-app.png "Website App")
