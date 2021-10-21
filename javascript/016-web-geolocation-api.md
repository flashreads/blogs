---
id: "016-web-api"
title: "Javascript Geolocation API"
tags:
- javascript
- api
- objects
- geolocation
date: 2021-10-21
keywords: javascript, objects, api
categories: 
- javascript
cover: ../../images/categories/javascript.png
author: Melo Noia
meta-description: Javascript Geolocation API
---

# Web Geolocation API
This API is used to determine the location of a user in web applications. The user must give the application permission for the location information to be accessed.


## Using Geolocation API

The ***navigator.geolocation*** object is used together with the ***getCurrentPosition()*** to get the user's current location.

The getCurrentPosition() can succeed or fail. It accepts three callbacks [success, error, options]. The last two callbacks are optional. 

```javascript
navigator.geolocation.getCurrentPosition(success, error, options);

```

### Example
```javascript
function success(position) {
  console.log(`Latitude : ${position.coords.latitude} Longitude: ${position.coords.longitude}`);
}

function error(err) {
  console.log(`ERROR: ${err.message}`);
}

navigator.geolocation.getCurrentPosition(success, error);

```
