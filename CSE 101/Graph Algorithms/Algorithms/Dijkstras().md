```
procedure GraphSearch(Dijkstra's)(G: directed graph with edge weights l, s:vertex):
	X = empty, F = {s}
	dist(v) = inf for all v
	dist(s) = 0
	While F is not empty:
		Pick v in F (any vertex)
		For each neighbor u of v:
			if dist(u)>dist(v)+l(v,u):
				move u to F
				set dist(u) = dist(v)+l(v,u)
		Move v from F to X
```