---
id: 033-insertion-sort-python.md
title: Insertion Sort in Python
tags:
  - python
  - insertion sort
  - sorting
  - algorithms
date: 2021-10-11 17:30:00 -0800
keywords: python, sorting, algorithms, insertion, sort
categories:
  - python
cover: ../../images/categories/python.png
author: Ryan Lim
meta-description: insertion sort in python
---

# Insertion Sort in Python

[Insertion Sort](https://en.wikipedia.org/wiki/Insertion_sort) is type of [sorting algorithm](https://en.wikipedia.org/wiki/Sorting_algorithm) that is relatively simple to implement. It does not have the best runtime, i.e. `O(n^2)`, compared to more advanced sorting algorithms such as [quicksort](https://en.wikipedia.org/wiki/Quicksort) or [merge sort](https://en.wikipedia.org/wiki/Merge_sort) but is a good starting sorting algorithm to learn. It can be used to sort smaller arrays consisting of strings or numbers.

## Pseudocode

Here is the pseudocode of insertion code (from [wikipedia](https://en.wikipedia.org/wiki/Insertion_sort#Algorithm)):

```
i ← 1
while i < length(A)
    j ← i
    while j > 0 and A[j-1] > A[j]
        swap A[j] and A[j-1]
        j ← j - 1
    end while
    i ← i + 1
end while
```

The general idea behind it is to iterate through the array from beginning to end and swaps each element from the current element to the beginning of the array if a "greater" prior element is found compare to the current element. It basically sorts "subsections" of the array repeatedly until the entire array is sorted by "inserting" new elements in the right order in the subsection of the array.

## Python Implementation

Without further ado, here is my Python (3) implementation of it:

```python
def insertion_sort(array):
    for i in range(1, len(array)):
        j = i
        while j > 0 and array[j - 1] > array[j]:
            # swap the two array elements
            temp = array[j - 1]
            array[j - 1] = array[j]
            array[j] = temp
            j -= 1
    return array
```

As you can see, it closely follows the pseudocode, with some minimal code savings using the `range` function. The `swap` was implemented inline but could be implemented as a separate function as well.

## Runtime

As mentioned, the average runtime for this algorithm is `O(n^2)`. The best case is an array that is already sorted with a runtime of `O(n)` as the current element in the array will only be compared once with a prior element. The worst case is an array that is sorted in reverse as each new element will need to be compared (and swapped) with every prior element to the beginning of the array.

Thanks for reading, any comment or feedback is most welcome!
