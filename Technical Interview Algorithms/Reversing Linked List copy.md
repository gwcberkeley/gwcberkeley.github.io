---
title: Reversing Linked List
parent: Technical Interview Algorithms
has_children: false
nav_order: 2
---

# Reversing Linked List

This is an algorithm that you should probably memorize its code. The idea is that we use two pointers to keep modifying the list while keeping track of the place we are not yet modified. 


The actual code is short for reversing linked list, but it is usually a small and crucial portion in a complex linked list problem.


### Skeleton Code

```python
def reverse(lst):
	prev = null
	while lst:
		next = lst.next
		lst.next = prev
		prev = lst
		lst = next
```


### Examples

Palindrome linked list