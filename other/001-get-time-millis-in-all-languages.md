---
id: 001-get-time-millis-in-all-languages.md
title: Get current time in milliseconds in all popular programing languages
tags: current-time, millis, milliseconds, python, javascript, java, golang, c-sharp, c++, scala, kotlin, ruby
author: Pavle Jonoski
meta-description: The definitive guide on how to get current time in milliseconds in (almost) all programing language that you'll ever use.
---

Get the current time as milliseconds in:
* [Python](#python)
* [JavaScript](#javascript)
* [Java](#java)
* [Swift](#swift)
* [Go](#go)
* C#
* C++
* Scala
* Kotlin
* Ruby
* PHP
* C
* Rust
* Objective-C
* Dart
* Lua
* Haskell
* Clojure
* Matlab/Octave
* R


# Python

```python
import datetime

# Microseconds precision, returned as float number
curr_time_millis = datetime.datetime.now().timestamp()*1000

print(curr_time_millis) 
>> 1590571047186.401
#  [ millis    ].[ microseconds]

# Get just the milliseconds
curr_time_millis = int(datetime.datetime.now().timestamp()*1000)

print(curr_time_millis) 
>> 1590571047186
```

# JavaScript

```javascript

currTimeMillis = new Date().getTime() // returns unix timestamp in milliseconds

console.log(currTimeMillis)
>> 1590571047186

```

# Java

```java

long currTimeMillis = System.getCurrentTimeMillis();

System.out.println(currTimeMillis);
>> 1590571047186
```

# Swift

```swift
var currTimeMillis = Int64(NSDate().timeIntervalSince1970 * 1000)

>> 1590571047186
```

Swift 3.0

```swift
var currTimeMillis = Int64(Date().timeIntervalSince1970 * 1000)

>> 1590571047186
```

# Go

```go

```