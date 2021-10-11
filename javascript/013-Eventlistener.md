---
id: 013-Eventlistener
title: Eventlisteners and its use
tags: Javascript, es6, Event,function
date: 2021-11-10 10:30:39 +0200 
keywords: Javascript, es6, Event,function
categories: Javascript
cover: 
author: Harshvardhan Rathore
meta-description: brief overview of the blog entry (SEO optimization)
---

# EventListener in Javascript
An Eventlistener is a method in JavaScript that attaches an event to to an element.
The listener is programed to start an event when the input or signaling the event handler.

Syntax:-
element.addEventListener(event, function, useCapture);

some EventListeners are :-
onload //when the page loads
onclick //when a user clicks something
onmouseover //when a user mouses over something
onmouseup //when a user mouses down from something
onmousedown //when a user mouses up from something
onmouseout //when a user mouses out something
onfocus //when a user puts the cursor in a form field
onblur //When a user leaves a form field



```Events in javascript  
  // On clicking button this  function works
 <button id="btn" onclick="clicked()">Click me</button>
    function clicked() {
      console.log("The button was clicked.")
    }

 // On loading page this  function works
    window.onload =function(){
      console.log("The document was loaded.");

    }

    let ids = document.getElementById("firstcontainer")
    ids.addEventListener('click', function(){
       console.log("clicked on container");
    })

    ids.addEventListener('mouseout', function(){
      console.log("mouseout container");
    })

    ids.addEventListener('mouseover', function(){
      console.log("mouse on container");
    })

    ids.addEventListener('mouseup', function(){
      console.log("mouseup clicked on container");
    })

    ids.addEventListener('mousedown', function(){

      console.log("mousedown clicked on container");
    })
```

You can add many event handlers to one element.

## The removeEventListener() method

```
body.removeEventListener('click', bodyClickHandler);
// on each click of the page, you will no longer see a message
```
we use the removeEventListener method correctly. This time when a click event occurs, removeEventListener will remove the function bodyClickHandler which effectively eliminates the listener, and no clicks will generate a message.
