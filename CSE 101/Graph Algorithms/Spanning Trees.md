---
aliases:
  - Spanning Tree
---
A spanning tree of an undirected graph G=(V,E) is a subgraph G'(V,E') such that
- G' is a tree and
- all vertices in V are connected
- An output tree of DFS or BFS is a spanning tree

Minimum spanning Trees are spanning trees that have the lowest combined edge weights

Proof: The minimized graph is always a tree
- Assume there are connected minimum spanning graphs that's not a tree
- Then there is a cycle
- cut away cycle edges and the graph stays connected
- but it reduced the cost compared to the original
- so the original wasn't a minimum, but it assumes minimum
- contradiction

Two ways to find minimum Spanning Trees

### Prims
Pick the next lightest edge that keeps the graph connected and does not create a cycle
![[Prims()]]

### Kruskals
Pick the next lightest edge that doesn't create a cycle
![[Kruskals()]]