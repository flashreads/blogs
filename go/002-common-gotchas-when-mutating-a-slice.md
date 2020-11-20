---
id: 002-common-gotchas-when-mutating-a-slice
title: Common gotchas when mutating a slice
tags:
  - go
  - golang
author: Mina Gyimah
meta-description: Easy mistakes when mutating a slice in Go, and how to avoid them.
date: 2020-10-28 15:16:13 +0000
keywords: go, golang
template: post
categories:
  - go
cover: ../../images/categories/go.png
---

# Common gotchas when mutating a slice

Mutating slices in Go can be a bit confusing.

It's generally known that slices are a reference an underlying array. But when it comes to mutating a slice, there are some very common gotchas that can trip you up. Let's look at three scenarios.

## From inside a function
In Go, all variables are passed by value, meaning the function body will receive a copy.

When you pass a slice to a function, the variable (slice descriptor), is a **copy of the caller's reference** to the underlying array (by `caller` I mean the place where the function is being called).

So if you try to append to the slice inside the function, you are actually appending to a duplicate of the original reference. The caller's slice will remain unaffected.

In the example below, we try to append a value to a slice, using the `addNum` function. Unfortunately, after calling `addNum`, the slice hasn't changed.

```go
// THIS WON'T WORK
mySlice := []int{1,2,3}

func addNum (s []int, num int) {
	s = append(s, num)
}

addNum(mySlice, 4)

fmt.Println(mySlice)

// --> [1 2 3]
```

To successfully append to the slice, the function must return its copy of the slice. You then assign it to the original slice.

```go
mySlice := []int{1,2,3}

func addNum (s []int, num int) []int {
	return append(s, num)
}

mySlice = addNum(mySlice, 4)

fmt.Println(mySlice)

// --> [1 2 3 4]
```

## From inside a for-loop
When ranging over a slice, the variable referencing each value points to **a copy of the value**. If you try to mutate the value at a given index with this variable, it will not work. Once you leave the scope of the for-loop, you'll find the slice was unaffected.
```go
// THIS WON'T WORK
somePeople := []string{"Ada", "Grace", "Charles"}

for _, name := range somePeople {
	name = strings.ToUpper(name)
}

fmt.Println(somePeople)

// --> ["Ada" "Grace" "Charles"]
```
For the mutation to stick, you must use bracket notation instead:
```go
somePeople := []string{"Ada", "Grace", "Charles"}

for i, name := range somePeople {
	somePeople[i] = strings.ToUpper(name)
}

fmt.Println(somePeople)

// --> ["ADA" "GRACE" "CHARLES"]
```

## When using variables
This is similar to the for-loop example. Any changes to a slice require the use of bracket notation. **Variables will point to copies of the value** at a given index, meaning any changes to that variable will not affect the slice.
```go
// THIS WON'T WORK
type food struct {
	name   string
}

pantry := []food{
	{name: "banana"},
	{name: "satsuma"},
	{name: "kiwi"},
}

toChange := pantry[2] // this makes a copy!
toChange = food{name: "strawberry"}

fmt.Println(pantry)

// --> [{banana} {satsuma} {kiwi}]
```
With bracket notation, it works.
```go
type food struct {
	name   string
}

pantry := []food{
	{name: "banana"},
	{name: "satsuma"},
	{name: "kiwi"},
}

pantry[2] = food{name: "strawberry"}

fmt.Println(pantry)

// --> [{banana} {satsuma} {strawberry}]
```