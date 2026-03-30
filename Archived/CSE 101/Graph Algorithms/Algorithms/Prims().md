### High Level
Initialize an array called cost(v) = $\infty$ for all vertices
Pick any vertex s to start from. cost(s)=0
put s in X
repeat until all vertices are in X:
- For all vertices v not in X, update cost(v) to be the weight of the lightest edge connecting it to a vertex in X
- Find the minimum edge that has 1 vertex in X and 1 in U (find the vertex outside of X that has the lowest cost)
- Move the endpoint that is in U to X (envelop the lowest cost vertex from U to X, that vertex has to be connected to a vertex from X)
- add the edge to the output

### Medium Level

Very similar to Dijkstras. We'll use cost(v) instead of dist(v)

```
procedure Prims(G:undirected graph with edge weights):
	Pick random vertex s
	
	init X={},F={s}
	init cost(all) = inf
	init cost(s)=0
	init prev(s)=null
	init output = empty
	
	While F is not empty:
		pick v in F that has the lowest cost(v) value (use PQ)
		For each neighbor u of v:
			if cost(u)>l(v,u):
				move u to F
				set cost(u)=l(v,u)
				set prev(u) to v
		move v from F to X
		move l(v,prev(v)) into output
```

### Runtime
Same as dijkstras() 
both $O(deletemin|V|+decreasekey|E|)$

![[Dijkstras()#^9e16c5]]