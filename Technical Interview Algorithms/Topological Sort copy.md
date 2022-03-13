---
title: Topological Sort
parent: Technical Interview Algorithms
has_children: false
nav_order: 2
---

# Topological Sort

Here is a typical topological sort example.


Suppose we have a graph, and we want to visit all the nodes. However, we could not visit node X unless we have already visited all of X’s prerequisites. Every node X could have a different set of prerequisites, and they may overlap. How would you visit every node in the graph by visiting its prerequisites first?

### Skeleton Code

```python
def sort(args):
	parents = hashmap: (key -> set of parents of key)
	children = hashmap: (key -> set of children of key)
	Initialize an empty queue

	Go through data and add to both parents and children map
	Add all nodes with 0 parents to the queue

	result = []
	while not queue.empty():
		curr = queue.pop()
		result.append(curr)
		for every child in children[curr]:
			remove curr from parents[child]
			if parents[child] is empty:
				add child to queue
	return result
```

### Examples

Course Schedule