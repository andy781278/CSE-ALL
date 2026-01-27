```
procedure GraphSearch(Dijkstra's)(G: directed graph with edge weights l, s:vertex):
	X = empty, F = {s}
	dist(v) = inf for all v
	dist(s) = 0
	H = make PQ
	While F is not empty:
		u=deletemin(H)
		For each neighbor u of v:
			if dist(u)>dist(v)+l(v,u):
				move u to F
				set dist(u) = dist(v)+l(v,u)
				decreasekey(G,u)
		Move v from F to X
```

### Correctness Proof
Claim: After Dijkstra, dist(v) is the length of the shortest path from s to v for all vertices $v \in V$.

Proof by Contradiction

Suppose after Dijkstra finishes, for some vertex v, there is a path p from s to v such that length(p)<dist(v), or that the actual length is shorter than what we think. d(v) is the actual distance of v, length(p) at v = d(v).

This means that there must be a pair of connected values z and w that are between s and t such that d(z) = dist(z) and d(w) < dist(w)

Case 1: d(w) = d(z)+l(z,w). In other words, the actual distance to w is distance from z plus edge weight between them, or that the actual path goes through z to w. If this happens, then dist(w) > d(z)+l(z,w), or dist(w)>d(w). In the algorithm, when this happens, it is instructed to update the dist(w) to d(w). Contradiction states that dist(w)>d(w), but it has to be equal, so contradiction.

Case 2: d(w) < d(z) + l(z,w). In other words, the actual distance to w is already less than the distance to z plus edge weight between them. This also means that this  path is not the shortest path. Then there must be a shorter path. But we are assuming that this is the shortest path, so a contradiction.

### Run time
There is an issue if you pick v in F willy-nilly, so we instead pick the shortest dist(v) value.

Claim: Let d(v) be the length of the shortest path from s to v. Then after every iteration, dist(v)=d(v) for all vertices v in X. (after v goes to X, it is never going back to F. Therefore, a vertex enters F at most once.)

Base Case: the first vertex to move to X is s. dist(s)=d(s)=0.

IH: After k vertices have been moved to X, dist(v)=d(v) for all v in X.

IS: Suppose u is the next vertex to move to X (we want dist(u)=d(u))
- Suppose by contradiction that dist(u)>d(u)
- so there is a shorter path P where length(P) = d(u)
- In this path p, it still needs to start from s, which is in X and leave X to get to u.
- Therefore there must be vertices w and y such that w from X goes to y outside X
- w is in X, so d(w)=dist(w) by IH
- dist(y)>=dist(u) by choice of u
- Therefore d(u)=length(P)>=dist(w)+l(w,y)>=dist(y)>=dist(u)>d(u)
- This results in d(u)>d(u), which isn't possible

We use a PQ for so we can pick the shortest dist(v) value

$O((deletemin)*|V|+(decreasekey)*|E|)$

**Runtime of PQ**
deletemin: O(|V|)
decreasekey: O(1)

We can make it quicker if we implement a Binary Heap for the PQ.

![[Binary Heap]]

Now:
deletemin: O(log(|V|))

|                                         | Array        | Binary Heap            |
| --------------------------------------- | ------------ | ---------------------- |
| Sparse Graphs \|E\| = $\Theta(\|V\|)$   | $O(\|V\|^2)$ | $O(\|V\|log(\|V\|))$   |
| Dense Graphs: \|E\| = $\Theta(\|V\|^2)$ | $O(\|V\|^2)$ | $O(\|V\|^2log(\|V\|))$ |

^9e16c5

So dense graphs, use array, sparse graphs, use binary heap