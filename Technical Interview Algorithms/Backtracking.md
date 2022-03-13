---
title: Backtracking
parent: Technical Interview Algorithms
has_children: false
nav_order: 2
---

# Backtracking

Backtracking is a special case of search algorithms like DFS.


Suppose we want to search a node. If the node we are currently at is not the one we want, we backtrack to the original node to search and restore the current node. The benefit of this approach is that we only modify one graph instead of creating a new graph each time the recursive function is called.


The general procedure would be: modify the current node, call a recursive function on the children nodes, and restore the current node.


### Skeleton Code

```python
def backtrack(n):
		if (n is a base case): return
		if (n is the solution we want): return output(n)
		
		generate the next node to look at and assign it to s

		while s is not null:
			Apply some value to the current node c
			backtrack(s)
			Remove the value from the node c
```


### Examples

[Subsets](https://gwcberkeley.github.io/Algorithms%20Problems/Subsets.html)

N-Queens

Word Break