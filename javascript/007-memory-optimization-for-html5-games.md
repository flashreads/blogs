---
id: 007-memory-optimization-for-html5-games
title: Memory optimization for HTML5 games
tags:
  - javascript
  - games
  - gamedev
  - beginner
  - memory
  - optimization
author: Daniel Kalevski
meta-description: Quick guide for basic memory optimization in HTML5 games
date: 2020-10-27 19:51:08 +0100
keywords: javascript, games, gamedev, beginner, memory, optimization
template: post
categories:
  - javascript
cover: ../../images/categories/javascript.png
---

## Intro:
Most of the games contains game logic where you need to instantiate a lot of objects from some class like particles that have short lifetime and needs to be destroyed.

## Problem:
JavaScript's model is based on garbage collection pattern. This means that the developer don't have dirrect control over allocated memory. Memory locations (variables) marked as `null` will be collected by garbage collector and removed from memory. But when garbage collector needs to dispose a lot of objects, takes a lot of processing time. Neceserry spent processing time is bad for the performance of the game.

In most cases the memory profile will be like this:

![fig2](https://user-images.githubusercontent.com/10467454/97344828-91c31700-1889-11eb-9afb-f5fe9c4fcb6d.jpg)


## How to fix that

Solution for this kind of problem is implementing [**Object pools pattern**](https://en.wikipedia.org/wiki/Object_pool_pattern). This implementation will help with reusing disposed objects instead of creating new ones.

After optimization:

![fig3](https://user-images.githubusercontent.com/10467454/97344857-9be51580-1889-11eb-9b09-b767b129fd18.jpg)


## Example

1. Import [object-pool](https://www.npmjs.com/package/object-pool) npm module by executing `npm install --save object-pool`

2. Replace old implementation
```javascript
class GameObject {

    speed = 1

    run() { /* your code */ }
}

let gameObject = new GameObject()
gameObject.run()
```

with:

```javascript

import pool from 'object-pool'

class GameObject {
    
    speed = 1

    run() { /* your code */ }
}

const gameObjectPool = pool({
    init: () => { // a factory method which should return a freshly created object.
        return new GameObject()
    },
    initSize: 10, // a number to specify the initial size of reserved objects in the pool
    
    disable: gameObject => {
        // reset gameObject properties to default values
        gameObject.speed = 1
    }
})

let gameObject = gameObjectPool.create()
gameObject.run()

```

For more detailed documentation for the library visit [the link](https://www.npmjs.com/package/object-pool).