---
id: "013-selecting-elements-from-dom"

title: "Selecting Elements From The DOM"

tags:
  - development

  - javascript

  - frontend

  - DOM

date: "10/10/2021"

keywords: javascript, frontend

categories:
  - javascript

cover: "../../images/categories/javascript.png"

author: "Seun Taiwo"

meta-description: "Selecting elements from the DOM with ease."
---

## What is the DOM?

Simply put, the DOM (Document Object Model) is the tree in the browser that keeps track of all elements (nodes) on the page as well as their attributes and properties.

At some point, you'd need to select an element from the DOM for various reasons. You might want to add an event listener, or change a style,etc. There are four main methods that can help us achieve this:

1. document.getElementById - Takes an Id and gets the first element with that Id.

2. document.getElementsByClassName - Takes a class name and gets all elements with that class name.

3. document.querySelector - Takes a query and gets the first element matching that query.

4. document.querySelectorAll - Takes a query and returns all elements matching that query.

Of the four methods above, the first two are the older and have been used for a very long time, hence, a lot of people know it and often teach it to others. I beg to differ though as my experience with 3 and 4 have been spectacular. They both take CSS-like queries as their input and working with them has greatly improved my speed. You can use them like so

```js
document.querySelector("div.box > p"); //Returns the p tag that is in a div with a class of box
document.querySelectorAll("section.card h2"); //Returns all the h2 tags that are children ( or grandchildren ) of
//  the section element with a class of tag
```

To get the elements we got in the code snippet above, we'd have to add new Ids or classes to our elements which I feel is unnecessary. If you aren't already using methods 3 and 4, I really do hope you switch. Thanks.
