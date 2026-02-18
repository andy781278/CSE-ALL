### High Level
- Given an undirected connected graph with positive edge weights:
	- start with only vertices
	- have a sorted PQ of the edges starting with the smallest edge weights
	- repeatedly add the lightest edge that does not create a cycle

How do we implement this efficiently?
How do we efficiently determine if the next lightest edge creates a cycle in X?
How do we efficiently determine whether or not a cycle is formed?

We use DSDS.
![[Disjoint Sets Data Structure|DSDS]]

Time Analysis
|V|makeset + 2|E|find + (|V|-1)union + sort(|E|)

#### Leader Implementation:
Keep an array for each vertex. Each index corresponds to a vertex, but the contents of the array points to the leader of their group. DSDS unionizes groups starting from individual level, so groups merge and leaders come out on top.
- Keep array Leader(u) indexed by element
- In each array position, keep the leader of its set
- Makeset O(1), Find O(1), Union O(|V|)
Total Time: $|V|O(1)+2|E|O(1)+(|V|-1)O(|V|)+sort(|E|)$
= $O(|V|^2+|E|log|V|)$
![[Pasted image 20260201112406.png]]

#### Union By Rank Implementation:
Instead of an array, we use a tree where the root is the leader. This way it is really easy to find the leader. Each vertex in the same tree is in the same graph, each vertex points to its parent, the root points to itself.
The actual information is stored in 2 arrays:
- $\pi(v)$: the parent pointer
- rank(v): the height of the tree hanging from v

- Procedure makeset(x) (O(1))
	- $\pi(x)$:= x
	- rank(x):= 0
- Procedure find(x) (O(height of tree)) O(logn)
	- while(x != $\pi(x)$)
		- x := $\pi(x)$
	- return x
- Procedure union(x,y) (O(find)) O(logn)
	- rx:=find(x), ry:=find(y)
	- if rx == ry then return
	- if rank(rx)>rank(ry) then
		- $\pi(ry)$:=$\pi(rx)$
	- else:
		- $\pi(rx)$:=$\pi(ry)$
		- if rank(rx) == rank(ry) then
			- rank(ry):=rank(rx)+1
![[Pasted image 20260201112330.png]]

##### Why are these trees short (efficient)?
Claim: If a vertex has rank k, it has height tree k
Proof:
Base Case: a vertex by itself has rank 0
Suppose that every vertex of rank k has tree height k
consider a vertex v of rank k+1, then it has have been a vertex of rank k at some point. It increased when another vertex u of rank k was unioned with v. The parent of u is v so that edge (u,v) along with the height of the tree hanging from u makes a tree of height k+1 hanging from v

Claim: Any root node of rank k has at least $2^k$ vertices in that tree
Proof:
Base Case: a root of rank 0 has 1 vertex
suppose a root of rank k has at least $2^k$ vertices in its tree
Then a root of rank k+1 can only be made by unionizing 2 roots each rank k. So a root of rank k+1 must have at least $2^k+2^k=2^{k+1}$ vertices in tree.

The max height of a tree is log(n) with n vertices

Run Time:
O(|E|log(|V|)) = O(|E|log(|E|))

Kruskals is as efficient as Prims

