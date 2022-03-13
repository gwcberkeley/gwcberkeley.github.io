---
title: Dijkstra’s Algorithm
parent: Technical Interview Algorithms
has_children: false
nav_order: 2
---

# Dijkstra’s

Dijkstra’s is an algorithm that finds the shortest paths from a single source to all other nodes in the graph. **The edges in the graph must be nonnegative.** You will encounter Dijkstra’s algorithm in CS61B and CS170. 


G = graph made up of set of vertices V and set of edges E
|V| = number of vertices in the graph
|E| = number of edges in the graph
Edge (u, v) means node u → node v
source = source node you are running dijkstra’s from


#### Skeleton Code

```python
def dijkstra's(G, source):
	initialize heap
	initialize list dist[n] with inf for all entries
	initialize list prev[v] with null for all entries
	for v in V:
		heap.insert(v, inf)
	dist[source] = 0
	PQ.insert(source, 0)
	while heap.size() > 0:
		u = heap.delMin()	#heap.pop(), where heap is sorted in increasing order
		for each (u, v) in E:
			if dist[u] + w(u,v) < dist[v]:	#w(u,v) is cost of edge(u,v)
				heap.insert(v, dist[u] + w(u,v))
				dist[v] = dist[u] + w(u,v)
				prev[v] = u
		return dist, prev

```


You can extract the shortest paths from the source to all other nodes using the prev array, and see the distances from the source to all other nodes in the dist array


#### Examples


Cheapest Flights within K Stops



Word Ladder