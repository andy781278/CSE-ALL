Explores every vertex reachable from s in G
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