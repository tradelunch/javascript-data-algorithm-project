# Detect a cycle in a Graph

### Background

> 1. If graph is a tree, there must be n - 1 edges when vertex is n.
> 2. There must be a cycle if the number of edges is greater or equal to n



### Detect a cycle with union find?

{% embed url="https://www.geeksforgeeks.org/introduction-to-disjoint-set-data-structure-or-union-find-algorithm/" %}



### How to check cycle?

* Count Edges
  * undirected only
* DFS
  * both possible
  * directed - white/gray/black
  * undirected - true/false
* Union Find - disjoint set
  * undirected only
  * no self loop
