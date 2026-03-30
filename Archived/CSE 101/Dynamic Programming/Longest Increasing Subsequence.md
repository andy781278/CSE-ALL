Given a seq of distinct positive ints a[1..n], an increasing subsequence is a seq a[i1..ik] such that i1<...<ik and ai1 < ... < aik

Using Shortest Path in DAG, we can solve this:
- What could the vertices be?
	- the values
- edge?
	- edge from ai to aj if i<j and ai < aj 
- weights?
	- -1

negative weights makes it opposite, so it finds longest instead of shortest, and each edge is weight 1 by default, so this finds longest increasing subsequence