---
aliases:
  - DSDS
---
DSDS manage partitioning the set into disjoint subsets
- Makeset(S): puts each element of S into a set by itself
- Find(u): returns the name of the subset containing u
- Union(u,v): unions the sets containing u and v.

### Kruskals with DSDS
```
procedure Kruskal(undirectd connected graph G, edge weights w):
	Makeset(v) for all v in V
	X={}
	Sort the edges in E in increasing order by weight
	For all edges (u,v) in E until X is a connected graph
		if find(u) != find(v):
			add edge (u,v) to X
			Union(u,v)
```