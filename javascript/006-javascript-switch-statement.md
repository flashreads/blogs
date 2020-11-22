---
id: 006-javascript-switch-statement
title: JavaScript Switch Statement
tags: javascript, es6, beginner,
author: Thomas Mwaka
meta-description: Learn how JavaScript switch statement works
---

## JavaScript Switch Statement.

The switch statement is used to perform different actions based on different conditions.
Use the switch statement to select one of many code blocks to be executed.
This is how it works:

-The switch expression is evaluated once.
-The value of the expression is compared with the values of each case.
-If there is a match, the associated block of code is executed.
-If there is no match, the default code block is executed.
    Example
The getDay() method returns the weekday as a number between 0 and 6.

(Sunday=0, Monday=1, Tuesday=2 ..)
The break Keyword
When JavaScript reaches a break keyword, it breaks out of the switch block.

This will stop the execution of inside the block.

It is not necessary to break the last case in a switch block. The block breaks (ends) there anyway.
The default Keyword
The default keyword specifies the code to run if there is no case match:

Example
The getDay() method returns the weekday as a number between 0 and 6.

If today is neither Saturday (6) nor Sunday (0), write a default message.