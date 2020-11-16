---
id: 004-LesserKnownHTMLTricks.md
title: Lesser Known HTML5 Tricks
tags:
  - HTML5
  - Web development
  - tricks
author: V Rahul
meta-description: Useful HTML tricks that we can use to write an effective code.
date: 2020-10-28 21:16:09 +0530
keywords: HTML5, Web development, tricks
template: post
categories:
  - html
cover: ../../images/categories/html.png
---

# Lesser Known HTML5 Tricks:

<br>
<br>

## 1.Editable Content:

```
<h1 contentEditable>Hello World</h1>
```

This feature lets you edit the content of element inside the browser just by clicking on the content. You must try!

<br>
<br>

## 2. HTML anchor element trick:

```
<a href=”skype:username?chat”>Start chat with the username</a>
<a href=”skype:username?call”>Start call with the username</a>
<a href=”skype:username?add”>Add username</a>
<a href=”mailto:someone@gmail.com">Send email</a>
<a href=”tel:00000000”>Make a call</a>
```

Here, just know I unfolded some of the things you can do with anchor tags that you may or may not be familiar with before reading this article. Well the good news is now you know these anchor element tricks! 
<br>
<br>

## 3.Refreshing browser after a specific time:

```
<meta http-equiv=”refresh” content=”10"/> 
```

Using this meta code you can refresh your webpage in the iterval of every 10 seconds. Isn’t that super cool? You can use it to make your browser refresh every 5 seconds while you do your CSS. You don’t have to refresh your browser manually to see the changes.

*Note: you can set content value to any value you like and it will increase or decrease the seconds based on the given value.*

<br>
<br>

## 4. Hiding elements without the help of CSS:

```
<h1 hidden>Hello World</h1>
```
Oh yess! Its true you can hide html elements without the help of CSS by using ‘hidden’ attribute. Also it doesn’t work like CSS hidden and what I mean by that is when we hide any element using attribute ‘hidden’ it works more like CSS “display: none” rather than “visibility: hidden”. It takes no space while CSS “visibility: hidden” only hides the element but still take up the space.

<br>
<br>

## 5. HTML prefetch webpage:

``` 
<link rel=”prefetch prerender” href=”” />
```

We know that after landing to the homepage the user is more likely to navigate to about page then you can prefetch the CSS files that will necessary for that webpage in the background before user even clicks on the link to navigate to that page. What it does is speeds up the process and user feels little to no delay in a reloading of a webpage.

<br>
<br>

*Happy Coding and Keep Reading, Cheers!*