---
id: 019-data-validation-using-joi
title: Performing Data Validation using JOI 
tags: 
  - javascript
  - data
  - joi
  - validation
date: 2021-10-23
keywords: javascript, data, web, joi, SQL injection
categories:
  - javascript
image: assets/images/javascript/data.svg
author: Victory Nwani
meta-description: Learn how to validate data using Joi to prevent SQL injection attacks.
categories:
  - javascript
---

# Data Validation in Node.js Applications Using Joi
 
 Every application built consists of data. Be it a Web, Mobile or even Console based application, data is either displayed or accepted from a user as an input. Before you store the user input recieved, data validation is highly recommended to prevent the risk of a malicious SQL query being executed on your database. You can perform the data validation directly from the client side application where the input is recieved, and also at your server side application, before the data is stored. A Node.js package which you can use to perform data validation in Node.js applications is Joi. 

 Let's proceed to get simplified understanding of Joi and see examples of how it can be used. 

## What is Joi? 
  
  As described in the [Joi](https://joi.dev/) documentation, "Joi is a data validator library for JavaScript". Joi's comprehensive API provides support for validating the data type of a value, and can also be extended to validate properties of a string. For example, checking the length of a string, or checking if a value is a valid email, or date within a specified range.

  The first step to take when using Joi is to construct a schema. At it's basics, a Joi schema is an object with fields that model the data being validated agaisnt. Let's proceed to construct a schema for a user's data within an imaginary application. 

## Modeling A User Data Schema
 For the imaginary application, we would expect that a user's data must contain the following three fields;

 - A name field containing a string data type that has a minimum length of 5 characters and a maximum character count of 25 
 - A description field similar to the name field, but has a minimum acceptable character count of 50 and maximum count of 300. 
 - An email field containing a string data type with the "@" character. The email must have a [Top Level Domain](http://data.iana.org/TLD/tlds-alpha-by-domain.txt) (TLD) of ".com". A TLD is the last part of a domain, that is after the dot (.) character. 

```JavaScript
  const Joi = require("joi")

  const userSchema = Joi.object({
    name: Joi.string().min(3).max(25).required(),
    description: Joi.string().alphanum().min(50).max(250).required(),
    email: Joi.string().email({
      tlds: { allow: ["com"] }
    }).required()
  });
```

**Note:** Based on the needs for your application, you might have more fields within your schema. Visit the API section of the Joi documentation for a complete list of Joi's API.

## Validating Values Using The Schema 

At this point there is now a `userSchema` variable contain a Joi schema that models a user application. Let's go through the next code snipet below that explains how the schmea can be used.

You can validate data using the schema by calling the [assert](https://joi.dev/api/?v=17.4.2#assertvalue-schema-message-options) method within the schema object and passing in the data to be validated agaisnt. The snippet below demonstrates how this is done; 

```JavaScript
const validateData = ({ name, description, email }) => {
  try {
     Joi.assert({ name, description, email }, userSchema);
  } catch (e) {
    console.log(`Erorr validating data: ${e}`)
  }
}

validateData({
   name: "John Doe",
    description: "Some pretty long and organized description of me the author",
    email: 'john.doe@gmail.com'
})
```

When the `validateData` function in the code snippet above is executed, the `name`, `description` and`email` arguments passed to the function will be validated using the [assert](https://joi.dev/api/?v=17.4.2#anyvalidatevalue-options) method in the [try/catch](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch) block. If the values don't meet up with the validation standards, an exception will thrown and handled the catch block.


This forms the basic usage of the Joi Schema to for validating your data. You can also use the [validate](https://joi.dev/api/?v=17.4.2#anyvalidatevalue-options) and [attempt](https://joi.dev/api/?v=17.4.2#attemptvalue-schema-message-options) methods depending on your application's needs.