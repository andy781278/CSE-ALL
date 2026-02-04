---
aliases:
  - Graph Reachability
---
# High Level
Includes BFS, DFS, Dijkstras, ...

![[explore()]]
# Mid Level

# Data Structures (Low Level)
### Frontier (F)
##### F as a Stack

prev keeps track of where the vertex came from (makes a path)
previsit/postvisit are ints, it keeps track of the order of the traversal
![[Screen Shot 2026-01-12 at 9.08.42 PM.png]]
You can construct a DFS output tree, but it misses info about the back edges
![[back edges]]
theorem: an undirected graph G has a cycle iff its DFS output has back edges
An undirected graph is connected if every vertex can reach every other vertex through a path.
![[DFS()]]

##### F as a Queue

Proving these shortest path algorithms require two parts:
- Path Correspondence: establish the types of objects you are trying to minimize in the original problem correspond to the paths in the graph you built (Bi-directional)
- Optimality: If you have done the path correspondence, then say "There can't be anything better than this because Dijkstra would have found the best path..."

![[BFS()]]

##### F as a Priority Queue
![[Dijkstras()]]