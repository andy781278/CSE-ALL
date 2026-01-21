---
aliases:
  - Graph Reachability
---
# High Level
Includes BFS, DFS, Dijkstras, ...
Try to go through the graph and all nodes.

X: eXplored, F: frontier, U: unreached
```
procedure GraphSearch(G:graph,s:vertex)
	Initialize V=G.getAllVertexes, X=empty, F={s}, U=V-F
	While F is not empty:
		Pick w in F
		For each outgoing neighbor y of w:
			if y is not in X or F (not explored yet), then move y from
			U to F (so we can explore it later)
		Move w from F to X
		
	U are all the nodes that you can't get to
	X are all the nodes that can be reached
```

X is a set, array of booleans index is vertex
F is a set, Stack or Queue + array of booleans
U is a set, array of booleans

G is a graph in adjacency list form

Total runtime (Worse Case):
### $$\sum_{w \in V} c+c'*(out)deg(w)+c''$$
$$=(c+c'')|V|+c'\sum_{w\in V}outdeg(w)$$
$$=O(|V|)+O(|E|)=O(|V|+|E|)$$
E -> all the edges

Proof:
- At the end of the algorithm:
	- A: if $v \in X$ then there is a path from s to v
		- Prove Loop Invariant: After t iterations of the while loop, every element in X or F is reachable from s in G
		- Base Case: before any iterations, there is no element in X, and only s is in F, and s can reach itself, so this is true
		- Pick some vertex v in F, we move all of the neighbors of v into F if they are in U. We assume there is a path from s to v because v is in F, v can only be in F if there is a path from s to v.
		- Then, we move v from F to X,.
		- Do this for every vertex, and we'll see that every v in F and X is reachable from s
	- B: if $v \notin X$ then there is not a path from s to v
		- Contrapos: If there is a path from s to v, then $v \in X$.
		- suppose by contradiction that there is a path from s to v but $v \notin X$. 
		- Let z be the latest vertex to be added to X, and w is added in X right after.
		- Then z must have been in F, because you can only move vertexes from F to X. When z is moved to X, it must bring its neighbors along, which includes w. So w must also be in X.
		- if w is in X, that means it can be a z, and its neighbors, the new w, must also be in X, this eventually goes down to v, which has to be in X.
		- There is a contradiction, so the opposite must be true.

# Mid Level
![[Dijkstras()]]

# Data Structures (Low Level)
### Frontier (F)
##### F as a Stack
 ![[explore()]]
prev keeps track of where the vertex came from (makes a path)
previsit/postvisit are ints, it keeps track of the order of the traversal
![[Screen Shot 2026-01-12 at 9.08.42 PM.png]]
You can construct a DFS output tree, but it misses info about the back edges
![[back edges]]
theorem: an undirected graph G has a cycle iff its DFS output has back edges
An undirected graph is connected if every vertex can reach every other vertex through a path.
![[DFS()]]

##### F as a Queue
![[BFS()]]

##### F as a Priority Queue