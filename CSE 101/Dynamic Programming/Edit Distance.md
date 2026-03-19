Find out closeness from one word from another by finding the amount of
- insertion
- deletion
- substitution
you need to transform one word to another

Ex: PELICAN to OSTRICH
- substitute each letter to the other, 7 sub
is there a better way?
![[Pasted image 20260317164017.png]]
6 changes, better, repeated "ic"

How to do it?

Brute force - try all combinations to find the optimal minimum cost, $3^n$ combinations, too long

1. Define sub-problems and corresponding array

let E[i,j] be the edit distance (min number of changes) to transform $x_1...x_i$ to $y_1...y_j$.

2. What are the base cases

E[0,j] = j, E[i,0] = i

3. Give recursion for sub-problems (case analysis)
(what does the last column of the transformation table look like)
Case 1: last col is deletion
- Then it'll go like this
	- x1, ..., xi-1,  xi
	- y1, ..., yj      -
- Therefore we  can say E[i,j]=1+E[i-1,j]
Case 2: last col is insertion
- same thing
	- x1, ..., xi,    -
	- y1, ..., yj-1, yj
- E[i,j]=1+E[i,j-1]
Case 3: last col is substitution
- if xi != yj
	- E[i,j]=1+E[i-1,j-1]
- else
	- E[i,j]=0+E[i-1,j-1]
	- because they're already the same

put it all together
- If xi=yj:
	- E[i,j]=min(E[i-1,j],1+E[i,j-1],0+E[i-1,j-1])
- else:
	- E[i,j]=min(E[i-1,j],1+E[i,j-1],1+E[i-1,j-1])

3. Order the subproblems, find the bottom-up order

to know E[i,j], we need E[i-1,j], E[i,j-1], and E[i-1,j-1]
we go through them all by starting from E[0,0] and increasing j, when it is filled, increment i, so we fill it in left to right, up to down, like writing

4. What is the final output

E[n,m] returns the minimum edit distance for n size to m size word

5. Put it all together into iterative alg that fills the array step by step

```
EditDist(x[1..n],y[1..m]):
	Init for i from 1 to n, E(i,0)=i and for j from 1 to m, E[0,j]=j (base cases)
	for i from 1 to n:
		for j from 1 to m:
			If xi=yj:
				E[i,j]=min(E[i-1,j],1+E[i,j-1],0+E[i-1,j-1])
			else:
				E[i,j]=min(E[i-1,j],1+E[i,j-1],1+E[i-1,j-1])
	return E[n,m]
```


6. Correctness Proof

You can make a graph and trace Dijkstra's to find shortest path that corresponds to the answer

7. Runtime Analysis

Graph has |V|=nm and |E|= 3nm, using Dijkstra's 
$O(nmlog(nm))$

There is a faster way if the graph is a DAG

![[Shortest Path in DAG]]

Using this, we can reduce it to O(|V|+|E|)
so O(4nm)