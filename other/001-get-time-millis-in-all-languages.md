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
* [C#](c%23)
* [C++](#c++)
* [Scala](#scala)
* [Kotlin](#kotlin)
* [Ruby](#ruby)
* [PHP](#php)
* [C](#c)
* [Rust](#rust)
* [Objective-C](#objective-c)
* [Dart](#dart)
* [Lua](#lua)
* [Haskell](#haskell)
* [Clojure](#clojure)
* [Matlab/Octave](#matlab/octave)
* [R](#r)


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

import (
    "fmt"
    "time"
)

func main() {
    currTimeMillis := time.Now().UnixNano() / int64(time.Millisecond)
    fmt.Printf("%d\n", currTimeMillis)
}

>> 1590571047186

```

# C#

```c#
long currTimeMillis = DateTimeOffset.Now.ToUnixTimeMilliseconds();
```

# C++

With C++ 11:
```cpp

#inclide <chrono>

using namespace std::chrono;

unsigned long long curr_time_millis = duration_cast<milliseconds>(
    system_clock::now().time_since_epoch()
).count();

```

With `time.h`

```cpp

#include <sys/time.h>


struct timeval tv;

gettimeofday(&tv, NULL);

unsigned long long curr_time_millis = 
    (unsigned long long) tv.time_sec * 1000 +  // time_sec is the number of seconds
    (unsigned long long) tv.time_usec / 1000;  // time_usec is the number of microseconds

```

# Scala

```scala

// same as in Java

val currTimeMillis = System.getCurrentTimeMillis();

// alternatively

val currTimeMillis = DateTime.now(DateTimeZone.UTC).getMillis()
```

# Kotlin

```kotlin
// Same as in Java
var currTimeMillis = System.currentTimeMillis()

// alternatively, using kotlin.system.getTimeMillis

import kotlin.system.getTimeMillis

var currTimeMillis = getTimeMillis()
```


# Ruby

```ruby
(Time.now.to_f * 1000).to_i
```


# PHP

```php
$curr_time_millis = round(microtime(true) * 1000);
```

# C

```c

#include <sys/time.h>


struct timeval tv;

gettimeofday(&tv, NULL);

unsigned long long curr_time_millis = 
    (unsigned long long) tv.time_sec * 1000 +  // time_sec is the number of seconds
    (unsigned long long) tv.time_usec / 1000;  // time_usec is the number of microseconds

```


# Rust

```rust

use std::time::{SystemTime, UNIX_EPOCH};

fn main() {
  let curr_time_millis = SystemTime::now().duration_since(SystemTime::UNIX_EPOCH).expect("We're before UNIX epoch.") * 1000;
  println!("{:?}", curr_time_millis);
}
```


# Objective-C

```objective-c
NSDate *date = [NSDate date];

double curr_time_millis = [date timeIntervalSince1970] * 1000.0;
```

# Dart

```dart
var currTimeMillis = DateTime.now().millisecondsSinceEpoch;
```


# Lua

Use the "socket" package
```lua
require "socket"
currTimeMillis = socket.gettime()*1000
```

# Haskell

```haskell
import Data.Time.Clock.POSIX (getPOSIXTime)


main = do
  currTimeMillis <- round . (1000 *) <$> getPOSIXTime
```


# Clojure

```clojure
(System/currentTimeMillis)
```

# Matlab/Octave

```octave
currTimeMillis = round(time() * 1000)
```

# R

```r
currTimeMillis = as.numeric(Sys.time())*1000
```