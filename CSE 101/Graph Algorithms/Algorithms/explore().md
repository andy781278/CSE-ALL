Explores every vertex reachable from s in G

Try to go through the graph and all nodes.

X: eXplored, F: frontier, U: unreached
```
Initialize a visited array of false for each vertex
procedure explore(G=(V,E),s):
	visited(s) = true
	previsit(s)
	component(s)=cc
	for each edge (s,u):
		if not visited(u):
			prev(u)=s
			explore(G,u)
	postvisit(s)
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
