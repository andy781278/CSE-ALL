What's the path from A to B in G that has the maximum bandwidth?

**Instance:** Directed graph G=(V,E) with positive edge weights, w(e), two vertices $s,t \in V$

**Solution type:** a seq of edges

**Constraints:** seq of eges is a path p from s to t in G

**Objective:** Over all possible paths p from s to t, find one that maxes BW(p) where $BW(p)=min_{e\in p}w(e)$ 


Two approaches:
##### Modifying existing alg
```
procedure MaxBand1(G:directed graph, s,t: vertices):
	B(v)=0 for v in V
	B(s) = inf
	While F is not empty:
		Pick v in F
		For each neighbor of v:
			m = min(B(v),w(v,u))
			if m>B(u):
				move u to F
				B(u)=m
		Move v from F to X
	return B(t)
```
This works, but the runtime gets complicated.
Also, we'll have to re-prove this

Proof:
- a: for all vertices $v\in V$ there is a path from s to v such that BW(p)=B(v)
- b: for all vertices $v\in V$ B(v) is the maximum bandwidth along all paths from s to v
##### Reducing existing alg input
- Usually a lot better because its got a stable foundation
- if it aint broke dont fix it
```
MaxBandDecision(G,s,t,M):
	Construct G_M by removing all edges less tham M from G
	run graphsearch(G_M,S)
	if t is visited return true
	else return false
```

Proof:
- a: if there is a path from s to t with bandwidth at least M then return TRUE
	- suppose that there is a path p from s to t in G with a bandwidth of at least M. Then every edge in p has weight greater than or equal to M. Therefore p is a path in $G_M$. So the alg will return true
- b: if there is not a path from s to t with bandwidth at least M then return FALSE
	- Contrapos: If alg returns TRUE then there is a path from s to t in G with a bandwidth at least M.
	- Suppose alg returns true, then there is a path p in $G_M$ from s to t. Then p is a path in G such that all edge weights are greater than or equal to M.

Time analysis:
MaxBandDecision(G,s,t,M):
- Time to create $G_M$: O(n+m)
- Time to graphsearch: O(n+m)
- Total time: O(n+m), linear
Find the max band:
- worse case, run MaxBandDecision m times
- Total time: O(m(n+m)), bad
- Better way: binary search the list of edges, use MaxBandDecision on the middle of a sorted list of edges
- This way it's O(log(m)(n+m)), this is the best way