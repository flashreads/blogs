---
id: 005-persistent-data-structures
title: Persistent Data Structures
tags:
  - data-structure
  - python
  - optimization
author: Pavle Jonoski
meta-description: What are persistent data structures? Learn in one minute.
date: 2020-10-28 14:42:44 +0100
template: post
categories:
  - other
cover: ../images/categories/other.png
---

# Persistent Data Structures

Persistent data structures are [data structures](https://en.wikipedia.org/wiki/Data_structure) that preserve the previous versions of the structure on modification.
They are effectively immutable, and depending on the implementation offer a special kind of memory optimization.

Being immutable, the persistent data structures are useful when writing concurrent code and the need arises to use some kind of data structure like list, tree, map or other.

When a persistent structure is modified, the original structure remains unchanged (it is a previous version), and the modification method returns a new structure that contains the modification.

Consider the following list:

```
a: 1 -> 2 -> 3
```

if we add another element to it, the list itself is modified:
```
a := add(a, 4)
a: 1 -> 2 -> 3 -> 4
```

However if we use a persistent list, then the same operation would look like this:

```
a: 1 -> 2 -> 3
b := persistent_list_add(a, 4)

print(a)
1 -> 2 -> 3

print(b)
1 -> 2 -> 3 -> 4
```

The method that adds an element to the list, actually returns a new list, containing the element we added.
The original list remains unchanged.

There are multiple ways that this can be achieved:
 
* Doing copy-on-write - we copy the entire list in `b` then actually add the element, leaving the original list `a` unchanged.
This however is not very memory efficient, as every modification would allocate memory for all previous elements - `O(n^2)` space complexity.
* Using a linked list, but we only keep the pointer to the head and the tail of the list. This way we can share the unmodified elements and
optimize the memory usage.

Let's consider the second way of implementing this data structure. We want to reuse the elements from `a` and just add the final element.

```
a: head a           tail a
   \                   |
    +-> (1) -> (2) -> (3)
   /                    \
b: head b                +-> (4) tail b
```

`a` and `b` share the first 3 elements, but only `b` can "see" the final added element.

When removing or updating an element, then we're only copying the list up to the affected elements.
Let's say we want to update the second element. Then we have to copy the head and the second element:

```
a: head a           tail a
   \                   |
    +-> (1) -> (2) -> (3)
   /               /    \
b: head b         /      +-> (4) tail b and c
                 /
    (1) -> (7) -+
     |
c: head c
```

After changing the element `2` to `7`, we have to copy all affected elements, but the rest of the list
remains unchanged and shared between the previous versions. Note that all changes return new versions of the
list and we cannot directly modify previous versions - `a` and `b` remain unchanged after we do `set(b, 2, 7)`.

## An example of persistent list in Python

Let's implement this kind of structure in Python. Every list would contain nodes that hold the data
and point to the next node. The list itself will contain the HEAD and TAIL nodes.

```python
class Node:

    def __init__(self, value):
        self.value = value
        self.next = None
    
    def __repr__(self):
        return str(self.value)

class PList:

    def __init__(self, head=None, tail=None):
        self.head = head
        self.tail = tail
    
    def add(self, value):
        '''Adds to the end of the list.
        '''
        node = Node(value)
        if not self.head:
            return PList(node, node)  # Add first element in an empty list
        
        self.tail.next = node

        # Return the new list
        return PList(self.head, node)
    
    def pop(self):
        '''Removes the last element from the list.
        '''
        if not self.head:
            raise Exception('Cannot pop from empty list')
        
        tail = self.head
        while tail.next != self.tail:
            tail = tail.next
        
        return self.tail.value, PList(self.head, tail)
    
    def update(self, index, value):
        '''Updates the element at index and returns the updated list.
        '''
        if not self.head:
            raise Exception('Empty list.')
        
        lst = PList()
        i = 0
        node = self.head
        while i < index and node != self.tail:
            lst = lst.add(node.value)
            node = node.next
            i += 1
        
        if i != index:
            raise Exception('Index out of bounds')
        
        lst = lst.add(value)

        lst.tail.next = node.next
        
        return PList(lst.head, self.tail)

    def remove(self, index):
        '''Removes the element at index.
        '''
        if not self.head:
            raise Exception('Cannot remove from empty list')

        if self.head == self.tail:
            if index == 0:
                return PList()
            else:
                raise Exception('Index out of bounds')

        lst = PList()
        node = self.head
        i = 0
        while i < (index - 1) and node != self.tail:
            lst = lst.add(node.value)
            node = node.next
            i += 1
        if i != (index - 1):
            raise Exception('Index out of bounds')
        if node.next == self.tail:
            # Actually pop
            return self.pop()
        
        tail = lst.tail
        tail.next = node.next
        
        return node.value, PList(lst.head, self.tail)

    def iterate(self):
        '''Returns an iterable (iterator) that goes through all elements of the list.
        '''
        if not self.head:
            return []
        node = self.head
        while node != self.tail:  # we must terminate at the tail of the list.
            yield node.value
            node = node.next
        yield node
    
    def __repr__(self):
        if not self.head:
            return '[]'
        return str([v for v in self.iterate()])


a = PList().add(1).add(2).add(3)
b = a.add(4)
print('Lists a and b after adding element to a:')
print('a:', a)
print('b:', b)

value, c = b.remove(2)
print('\nLists after removing element from b:')
print('a:', a)
print('b:', b)
print('c:', c, '(removed ', value, ')')

print('\nLists after updating element in b:')
d = b.update(1, 7)
print('a:', a)
print('b:', b)
print('c:', c)
print('d:', d)
```

After execution, it will print:

```
Lists a and b after adding element to a:
a: [1, 2, 3]
b: [1, 2, 3, 4]

Lists after removing element from b:
a: [1, 2, 3]
b: [1, 2, 3, 4]
c: [1, 3, 4] (removed  2 )

Lists after updating element in b:
a: [1, 2, 3]
b: [1, 2, 3, 4]
c: [1, 3, 4]
d: [1, 7, 3, 4]
```

which is exactly what we intended and wanted - every list is immutable and we can add/remove/update elements and
by doing so we get new lists.
