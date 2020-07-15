---
id: 001-delete-element-from-slice.go
title: Howto propoerly delete an element from a slice in Go
tags: go, golang, slice, delete
author: Pavle Jonoski
meta-description: Delete an element from a slice in Go properly and efficiently
---

# Properly delete an element from a slice in Go

Arrays and slices in Go are a bit different from analogous structrures in other languages (like `list` in Python).
An arrays is contigious container that holds the values, while the slice just holds pointers to the start and the end
of a region of the container that we're concerned about. Learn more about [slices and arrays in Go here](https://blog.golang.org/slices-intro).

This makes deleting a value from a slice a bit tricky.

There are two ways this can be achieved, depending on whether we want to keep the order of values in the array or not.

If we want to keep the order of the values, we can slice the array up to the element we want to remove, then append all
elements after the that:

```go

arr := []string{"a", "b", "c", "d", "e", "f"}

// we want to remove the thrid element "c"
i := 2
arr = append(arr[:i], arr[i+1:]...)

fmt.Println(arr)
// [a b d e f]
```

Note that we used the expansion expression `...` and we're adding the elements from the slice.

This gets the job done, but is not very efficient. However the order of the elements will be preserved.


If we don't care about the order of elements, we can swap the element we want to remove with the last element of the slice,
then make the slice to be one element shorter:

```go

arr := []string{"a", "b", "c", "d", "e", "f"}

// we want to remove the thrid element "c"
i := 2
arr[i] = arr[len(arr) - 1]
arr = arr[:len(arr) - 1]

fmt.Println(arr)
// [a b f d e]
// "c" is not in the slice, but the order is not preserved

```

This approach is *much* faster than the previous approach, but does not preserve the order of elements.

What is happening behind the scene: remember that in Go, arrays are the container holding the values, and the slice is just
a structure that points to the start and the end of the part of the array we're concerned about? In the second case what we
did was the following:

We started with something like this:

```
   
array: ["a"]["b"]["c"]["d"]["e"]["f"]
       ↑                          ↑
       |  ┌-----------------------┘
slice (0, 5)  start at 0 and end at 5
```

the slice starts at the 0th element and ends at the 5th element. The array is the background container holding the values.

After we swap out "c" with "f", we then set the slice end at 4 and end up with something likie this:

```
                   ┌---- swap ----┐
                   ↓              ↓
array: ["a"]["b"]["f"]["d"]["e"]["c"]
       ↑                     ↑
       |  ┌------------------┘
slice (0, 4)  start at 0 and end at 4

```
Now the slice ends at the 4th element. Note that the array still holds 6 values, however our slice only "sees" 5.