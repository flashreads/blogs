---
id: 001-flex-container.md
title: Getting Started with Flexbox
tags: css, Flex,
date: 2021-10-31 00:50:42 +0200 
keywords: css, flex, display,
categories: css, flex
cover: 
author: Igbinosa Iwinosa
meta-description: A brief introduction To CSS Flex
image: assets/images/css.svg
---

# Getting Started with CSS Flexbox

Flexbox is a layout method that consists of boxes that ... flex. Content is organized into boxes that can be scaled up and down and can be placed in rows and columns.

## What is CSS Flexbox?

Flexbox is a one-dimensional layout. That is, its properties and specifications are related to rows or columns. This is different from a CSS grid that has both rows and columns in two dimensions at the same time. You can use Flexbox to create grid layouts by nesting containers and elements.

## How to Use Flexbox
Flexbox consists of a alot of properties, the first step is using Flexbox is by invoking it with the display property.


```CSS
 display : flex;
```
Then we have the "flex-direction" property tells your container which direction its items should go in and therefore also says which direction the main-axis is going in. for example :-

```CSS
 flex-direction : column;
```
We also have the "flex-wrap" property which tells your code whether its items are allowed to wrap to the next line, like the lines on the page of a book, or whether they need to stay forced onto one line. an example is :- 

```CSS
 flex-wrap : wrap;
```
Flexbox has other Properties that you can learn here :- https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox