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

### Proving

#### Cut property
Suppose G'=(V,T) is a MST of G=(V,E), X subsets T.
S subsets V such that there is no route from S to outside S (V-S) using edges from X
Let $e \in E$ be the lightest edge connecting S to V-S
Then X U {e} must be a part of MST

Proof:
Case 1: $e \in T$
- Then X U {e} $\in T$

Basically, it cuts a graph into vertices that are in the tree, and the rest of them.
Then there's MST if you can add a new vertex into the tree

Prims connects the lightest edge from the current vertex that doesn't form a cycle, make two groups, one is the explored vertices, the other is not. Then the edge connects the known with the unknown.

Kruskals, group the vertices so that the new lightest edge that doesn't create a cycle connects two distinct vertex groups, doesn't matter how to group it, as long as the lightest edge connects two parts together, where the two groups are disjoint.

