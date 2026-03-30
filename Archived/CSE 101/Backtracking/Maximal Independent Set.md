Given graph G where edge between A and B means that they are enemies. Find the largest set of people such that no two are enemies.

Instance: Undirected Graph
Solution Format: Subset of vertices
Constraint: no two v in subset are connected by edge
Objective: Size of subset
Goal: Maximize

```
MIS1(G undirected):
	If |V|=0 return empty set
	pick v
	In = MIS1(G-{v and neighbors} U {v})
	Out = MIS1(G-{v})
	If |In| > |Out|:
		return In
	else:
		return Out
```

### Correctness
- Base Case: n=0, MIS1 returns empty set
- IH: let h>0, MIS1 correctly returns max ind set of any graph with k vert where $0\leq k<n$
- In is max ind set containing v
- Out is max ind set not v
- Better of two is MIS in G

### Time Analysis
Worse Case: T(n)=2T(n-1)+O(n)
$T(n)=O(2^n)$
Probably bad anyways, but better than brute force

## Get rid of stupid worst case

```
MIS2(G undirected):
	If |V|=0 return empty set
	pick v
	In = MIS1(G-{v and neighbors} U {v})
	If deg(v)==0:
		return In
	Out = MIS1(G-{v})
	If |In| > |Out|:
		return In
	else:
		return Out
```

$T(n)=O(1.62^n)$

## Get rid of other worst case

```
MIS3(G undirected):
	If |V|=0 return empty set
	pick v
	In = MIS1(G-{v and neighbors} U {v})
	If deg(v)==0 or deg(v)==1:
		return In
	Out = MIS1(G-{v})
	If |In| > |Out|:
		return In
	else:
		return Out
```

$T(n)=O(1.46^n)$

Best anyone has done is $O(1.2^n)$
