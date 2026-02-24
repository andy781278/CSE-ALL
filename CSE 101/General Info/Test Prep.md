
1. $n^2 \in O(2^n)$ -> true
2. $n^2 \in \Theta(2^n)$ -> false
3. $nlog(n) \in O(n^2)$ -> true
4. $n^2 \in O(nlog(n))$ -> false
5. $\sum^{i=n}_{i=1}i \in O(n)$ -> false
	- that converts to $\frac{n(n-1)}{2}$, which is $n^2$
6. $\sum^{i=log(n)}_{i=1}2^i \in O(n)$ -> false
	- $2^0+2^1+2^2 \in O(4)$
	- 1+2+4
	- the last element of the summation is equal to n, so it will always be worse
	
	- Correction: true
	- the pluses don't matter if its not at a higher order, so at most it is  equal, which is in equal or better
7. true
8. false
9. true
10. false
	- simple graph can have no edges, so it can always be better than V, which means its not same or worse
11. false
	- a vertex in a SCC can have incoming edges to each other in the SCC
12. true
	- I believe this is one of the properties of DAG
13. false
	- I thought it was source

14. Create graph G' by adding a vertex s to G, and connecting s to all $u \in S$ with an edge weight of 0.
	- Now run Dijkstra's starting on s. After it finishes, the node $v \in T$ with the smallest dist(v) number contains the smallest distance of any path starting from any  $u\in S$ and ends in some node $v\in T$.
	- For any path from some $u\in S$ to some $v\in T$, we can append the edge (s,u) to the beginning of the path to get a path of the same length from s to v in G'.
	- Conversely, for any path from s to some $v \in T$ in G', the first edge (s,u) for some $u \in S$ has an edge weight of 0, and the rest of the path is the exact same as in G.
	- Thus, the shortest path from some $u\in S$ to some $v \in T$ in G is the same length as the shortest length from s to v in G'.
	- Since G' has V+1 vertices and E+S edges, this makes time O((V+1+E+S)(logV))
	- O((2V+E)(logV))
	- O((V+E)(logV))
	- It takes O(V) to construct G' from G, since we just need to add a single list of size V to the adjacency list data structure.

15. If we run the first k iterations of the while loop of Dijkstra's starting on s, we retrieve the closest k vertices to s. This is a part of the correctness proof for Dijkstra's, which states that after every iteration, dist(v)=d(v) for all v in X. Every iteration, 1 v gets sent to X. So after k iterations. k vs gets set to X, and are all their final form. If they are also processed in order of closeness to s, then they are the k closest vertices to s.
16. Path length can mean total edge weight of the edges combined, or the amount of edges.
17. Suppose we model graph G after the city, where each intersection is a vertex, and each directed edge is a one-way street.
	- Run DFS on G, and print out a list of the post numbers for each $v \in G$.
	- If X != G, then set FS(v) = false for every $v \in G$.
	- let h be the vertex with the highest post number.
	- Create a reverse graph G', run explore through G' starting with h, let every reachable vertex to be $v \in S$ for an arbitrary set S.
	- Set FS(v) to be true for $v \in S$.
	- 
	- Creating G is O(|V|+|E|)
	- DFS is O(|V|+|E|)
	- Setting FS(v) = false for every v in G is O(|V|)
	- creating graph G' and exploring through it is O(|V|+|E|)
	- Setting FS(V) to be true for $v \in S$ is O(|V|)
	- All in all, O(|V|+|E|)

18. In a topological ordering ${v_1,v_2,...,v_k}$ for $v_i$ $\in G$, $i = \{1,2,...,k\}$, k=|V|, $post(v_i)\geq post(v_i+1)$. So run DFS on G, retrieve their post numbers, then compare their post number with the one after them. If its smaller, then it is not a topological ordering, so return false. If every vertex has a greater post number than the one after it, then return true.

19. Make G', the reverse graph of G, then run DFS through it. make an array of all $v \in G'$ ordered by descending post numbers. Run DFS on G based on the ordering of the array. Each time cc increments, it is a new SCC. As long as the SCC has at least 2 vertices, the vertices in that SCC are in a cycle with each other.

20. The only way to visit every vertex exactly once in a DAG is if there are no cross edges between any two vertices. This means every vertex has to be descendants or ancestors of one another, and the graph has to be completely linear. This can be detected by looking at the post numbers list after you run DFS. If at any time, two adjacent vertices don't have an edge between them, then there must be a cross edge somewhere.

21. Create a graph G', and for every vertex $v \in G$, create two copies: $v_0$ and $v_1$, and put them in G'. Additionally, for every edge $(u,v)$ in G, copy that, once for $(u_0,v_0)$, and another for $(u_1,v_0)$. After that, add edges $(u_0,v_1)$ for any 1 weight edges.
	- Then run explore on $s_0$ on G, if $t_0$ or $t_1$ ends up in X, then it work.
	- Proof: If algorithm returns true, that means there's a path from $s_0$ to either $t_0$ or $t_1$. 
		- Every path in G' corresponds to a path in G by construction
		- Case 1: $t_0$ is visited. This means that there's a path from $s_0$ to $t_0$ in G', which corresponds to s to t in G: $\{s,u_1,...,u_k,t\}$.
			- Lets assume by contradiction that there are two corresponding edges of weight 1 in that path, or $u_{i-1},u_i$, then $u_i,u_{i+1}$.
			- Then this corresponds to G': $(u_{0i-1},u_{1i})=1$, and $(u_{0i},u_{1i+1})=1$.
			- But this isn't possible since no $u_1$ can connect to any $u_0$. So  G' cannot exist.
		- Case 2: $t_1$ is visited, similar argument.
	- Proof: If there is a path from s to t in G that doesn't have two consecutive 1's, $p=\{s,u_1,...,u_k,t\}$, then the algorithm returns true.
		- Let's follow that corresponding path in G'.
		- We start with $s_0$, and for every 0 edge, we go from $u_{0i}$ to $u_{0i+1}$
		- If we encounter a 1 edge, then we go from $u_{0i}$ to $u_{1i+1}$.
		- The next edge after that must be a 0 edge, because no other edges exist.
		- We can use this argument for every 1 edge we encounter and build this corresponding path in G.
		- At the end of the path p, if it ends with a 0 edge, then it corresponds with $t_0$ in G', and algorithm returns true.
		- If it ends with a 1 edge, then the corresponding path in G' ends at $t_1$ and the algorithm also returns true.
	- This is linear time because:
		- Creating graph G' O(2|V|+3|E|)
		- explore on G' O(|V|+|E|)
		- In total, O(3|V|+4|E|)
		- O(|V|+|E|)
		- Linear

| PQ                | v   | ALB      | ATL      | AUS      | BOS      | CHI      | HOU      | LA       | PHX      | RAL      | SD  | SF       | DC       |
| ----------------- | --- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | --- | -------- | -------- |
| SD                |     | $\infty$ | $\infty$ | $\infty$ | $\infty$ | $\infty$ | $\infty$ | $\infty$ | $\infty$ | $\infty$ | 0   | $\infty$ | $\infty$ |
| LA, PHX, SF       | SD  |          |          |          |          |          |          | 100      | 350      |          | 0   | 500      |          |
| PHX, SF           | LA  |          |          |          |          |          |          | 100      | 350      |          | 0   | 500      |          |
| SF, AUS           | PHX |          |          | 1300     |          |          |          | 100      | 350      |          | 0   | 500      |          |
| AUS               | SF  |          |          | 1300     |          |          |          | 100      | 350      |          | 0   | 500      |          |
| HOU, ATL          | AUS |          | 2200     | 1300     |          |          | 1450     | 100      | 350      |          | 0   | 500      |          |
| ATL               | HOU |          | 2200     | 1300     |          |          | 1450     | 100      | 350      |          | 0   | 500      |          |
| RAL, DC, CHI, ALB | ATL | 3150     | 2200     | 1300     |          | 3000     | 1450     | 100      | 350      | 2600     | 0   | 500      | 2800     |
| DC, CHI, ALB, BOS | RAL | 3150     | 2200     | 1300     | 3300     | 3000     | 1450     | 100      | 350      | 2600     | 0   | 500      | 2800     |
| CHI, ALB, BOS     | DC  | 3150     | 2200     | 1300     | 3250     | 3000     | 1450     | 100      | 350      | 2600     | 0   | 500      | 2800     |
| ALB, BOS          | CHI | 3150     | 2200     | 1300     | 3250     | 3000     | 1450     | 100      | 350      | 2600     | 0   | 500      | 2800     |
| BOS               | ALB | 3150     | 2200     | 1300     | 3250     | 3000     | 1450     | 100      | 350      | 2600     | 0   | 500      | 2800     |
|                   | BOS | 3150     | 2200     | 1300     | 3250     | 3000     | 1450     | 100      | 350      | 2600     | 0   | 500      | 2800     |

Test 2

- input
	- $[x_1,...,x_n]$, all the stopping points, and distance d, the max dist you can travel per day
- solution format
	- $[p_1,...,p_k]$ list of stopping points to camp at
- constraints
	- no adjacent stopping points are more than d distance apart
	- $p_{i+1}-p_i \leq d$ for each i
- objective
	- The total amount of stopping points
- minimize

Exchange Argument
- let g be the first greedy choice, which is $p_1$, the first stopping point you camp at
- Consider an arbitrary solution AS that is legal and does not include g.
- Claim: There is a solution AS' that does include g and has less stopping points than AS

- we know g is the latest stopping point before you travel more than d distance. We know AS is valid, so it also has <= d distance between each of its stopping points.
- We make AS' by exchanging the first stopping point in AS with g.
- let's say AS = $[a_1,a_2,...,a_k]$, so AS' = $[g,a_2,...,a_k]$
- We know AS' meets the constraints because we know that $a_1$ has to come before g.
	- if $a_1$ comes after g, and is also legal (no more than d distance), then according to def of g, it should have been able to go that far as well, so there is no $a_1$ that can be after g.
- So we know g is legal, so from start to g is <= d, and that the distance between g and $a_2$ has to be less than $a_1$ and $a_2$, since g is more ahead that $a_1$, this makes the AS' legal.
- To show |AS'| <= |AS|, we have to indicate that it doesn't have to be 1 stop, g can surpass multiple stops. At the very least, it has to surpass 1 stop in AS, so it follows the construction of AS' that
- OS' = OS-{all stops before g in OS} U {g}
- therefore |AS'| <= |AS|

- input
	- n oxen $[Ox_1,Ox_2,..,Ox_n]$
- solution format
	- a list of pairings of the oxen
- constraints
	- no Ox can be in more than 1 team
	- in a pair $(Ox_i,Ox_j)$, $S_i+S_j \geq P$
- objective
	- the number of pairings
- maximize



Greedy strategy II is wrong:
[1,1,2,2,3,3], P=5
(2,3)(2,3)
(2,3)

Greedy Strategy I is correct:
- let g be the first pairing with the strongest and weakest oxen that meets the strength requirement, $g=(g_w,g_n)$
- let AS be an arbitrary solution that does not pick g, let it be $[(a1w,a1s),(a2w,a2s)...,(ajw,ajs)]$
- We make AS' by swapping the first pair with g.
- Then AS' has at least as many pairings as AS.
- AS' is valid because:
	- def g states that g meets the strength requirement
	- there are 4 scenarios:
		- gw and gn aren't any other pairings
			- then we need to change nothing, as it is already valid
			- also this would make AS' = AS+1
		- gw is in a pairing with sj with j != n, and gn is not paired
			- then destroy the pair and throw away sj, and put gw and gn together
			- this would make AS'=AS
		- gn is in a pairing with sj with j != w, and gw is not paired
			- then destroy the pairing and pair gn with gw
			- this would make AS'=AS
		- both gn is paired with sj, and gw is paired with si
			- then destroy both pairings and pair gn and gw together, and also pair si and sj together.
			- we know gn and gw is valid
			- si and sj is valid because:
				- we know that gw+si >= P, and we know that gw is the weakest, so sj>=gw, so replacing it would be sj+si>=P, transitiveness.

