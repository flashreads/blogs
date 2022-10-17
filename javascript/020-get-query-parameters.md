---
id: 020-get-query-parameters
title: Get query parameters in JavaScript
tags: javascript, query, URL
date: 2022-10-17 18:30:00 +0200 
keywords: javascript, java-script, js, query, url, params, parameters
categories: javascript
cover: assets/images/javascript/js2.svg
author: Pavle Jonoski
meta-description: Get query parameters in JavaScript
---

# Get query parameters in JavaScript

Query parameters are the parameters send in the URL itself, after the '?'.
They are separated with `&` and have the form of `param=value`.

There are many cases when we need to get some parameters from the current page URL, or other URL
in our code.

In JavaScript there are multiple ways of doing this:
* Use [`URLSearchParams`](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) interface provided by the Web API - supported all major browsers.
* Use [`URL`](https://developer.mozilla.org/en-US/docs/Web/API/URL) interface, also provided by the Web API and available on all major browsers.
* Use the [`url`](https://nodejs.org/api/url.html) module in nodejs.

## Use URLSearchParams to parse the query string of the URL

If you have the query string, you can use [`URLSearchParams`](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) to parse it, the use the [`get`](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams/get) method of the object to retrieve the needed parameter value:

```js

const q = new URLSearchParams('page=10&pageSize=20')
console.log('Page:', q.get('page'))
console.log('Page size:', q.get('pageSize'))

// output:
// Page: "10"
// Page size: "20"
```

## User the URL object

If you have the whole URL string, then you can parse it with [`URL`](https://developer.mozilla.org/en-US/docs/Web/API/URL).
The parsed URL object will contain `queryParameters` field which contains the parsed query parameters.

Example:
```js

const url = new URL('http://example.com?page=10&pageSize=20')

console.log(url.searchParams) // object of type URLSearchParams

// Get the parameter values
console.log('Page:', url.searchParams.get('page'))
console.log('Page size:', url.searchParams.get('pageSize'))

// output:
// Page: "10"
// Page size: "20"
```

Note that the `searchParams` field on the `URL` object is in fact of type `URLSearchParams`, just like in the first example above.

## Get query parameters in node.js

In nodejs, you can use the API from the provided [`url`](https://nodejs.org/api/url.html) module.

This module also provides a URL class that can parse full URLs:

```js
const url = require('url')

const u = new url.URL('http://example.com?page=10&pageSize=20')
console.log('Page:', u.searchParams.get('page'))
console.log('Page size:', u.searchParams.get('pageSize'))

// output:
// Page: 10
// Page size: 20
```

Note that, similar to the browser's Web API, the `searchParams` object in the parsed `URL` is of type `URLSearchParams` - the same interface as the one from the Web API in the browser, only this one comes from nodejs own `url` module.
