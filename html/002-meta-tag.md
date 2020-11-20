---
id: 002-meta-tag.md
title: HTML Meta tag viewport
tags:
  - html
  - tags
  - meta
  - viewport
  - meta-tag
author: Zoran Pandovski
meta-description: Quick explanation about when to use html tag <meta name="viewport">
date: 2020-06-17 22:56:16 +0200
keywords: html, tags, meta, viewport, meta-tag
template: post
categories:
  - html
cover: ../../images/categories/html.png
---

The `meta name=viewport` is not part of any web standards, but most of the mobile browsers today have support for it. The [meta tag](https://www.w3.org/TR/2011/WD-html-markup-20110113/meta.name.html) adds instructions to the browser about the page scaling on different devices. To optimize the webpage for mobile devices add:

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```
>Note: meta tag should be added in the <head> of HTML page.

The content `width=device-width` will set the width of the page the same as the device screen size and `initial-scale=1.0` will set the initial zoom on load. This means it will scale on different devices since the viewport(the visible area to the user) is different on the laptops, mobile phones, tablets. Omitting the `viewport` the browser will use a virtual viewport that will zoom out the website. So, it is always the best practice to add a viewport so the website will be optimized for different screens.