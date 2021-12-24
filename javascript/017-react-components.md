---
id: "017-react-js-components"
title: "React JS Components"
tags:
  - javascript
  - library
  - frontend
  - DOM
  - components
date: 2021-10-21
keywords: javascript, library, frontend, DOM, components
categories:
  - javascript
image: assets/images/javascript/react.svg
author: Marie-Claire
meta-description: React JS Components
---

# React JS Components

## React JS

React is a Javascript library created by Facebook in 2013. It is used to create user interfaces and UI components. React JS is a popular library used by companies such as Reddit, Salesforce, Hulu, and Netflix due to its ability to create fast and dynamic websites.

## Components

A component is a reusable peice of code. Much like a function, it is able to take in an input (props) to generate an output (React element).

In the example below, the `name` prop is passed into the Greeting component so that the Greeting component
can be reused multiple times with different names without repeating code.

```JSX
import React from "react";

const Greeting = ({ name }) => {
  return (
    <h1>Hello {name}, I hope you're having a great day!</h1>
    );
};

export default Greeting;
```

Here is an example of the Greeting component being invoked with different names:

```JSX
import React from 'react';
import Greeting from './Greeting';

const App = () => {
    return (
        <div>
            <Greeting name="Alex"/>
            <Greeting name="Rachel"/>
            <Greeting name="John"/>
            <Greeting name="Sammie"/>
        </div>
    );
};

export default App
```
