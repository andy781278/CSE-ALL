
```
procedure BFS(G,s):
	for each vertex u in V:
		dist(u)=inf
	dist(s)=0
	queue Q={s}
	while Q is not empty:
		pop u from Q
		look at all its neighbors, for each neighbor:
			set their distance to dist(u)+1
			put them into Q (alphabetical order)
```

Works on finding the shortest distances on graphs of equal edge weight

Proof of correctness
- For each vertex v, we want to prove that dist(v) is the minimum distance of all paths from s to v
- Claim: for each distance value d=0,1,2..., ***there is a moment*** in the algorithm when:
	1. all vertices at distance $\leq$ d from s have their distance values correctly set
	2. all other vertices have distances set to $\infty$
	3. The queue contains exactly the nodes at distance d
- Proof:
- Base Case (for d=0):
	1. dist(s) = 0 is the correct distance value
	2. all other vert is dist $\infty$
	3. the queue contains only s which is dist 0
- Induction Step:
	- Let k be arbitrary int such that $k\geq0$. Assume that the above three statements are true for when d=k.(prove it is true for d=k+1)
	- All vertices distance $\leq$ k have been set and the queue contains only vertices at distance=k
	- Suppose v is next vertex to be popped and let u be a neighbor of v
		- if dist(u) is $\infty$, then dist(u) becomes dist(v)+1 or k+1
		- if dist(u) is not $\infty$, then dist(u) is already set correctly by hypothesis
	1. All new vertices added to the queue have dist k+1 and are set correctly
	2. all vertices of distance k+1 have been added to the queue
	3. the queue only contains the nodes at distance k+1

Runtime:
O(|V|+|E|), since each vertex at most enters the Queue 1 time
