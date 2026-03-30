Given a list of real numbers
$$a_1,a_2,...,a_n$$
Look for 3 indices, (i,j,k), such that 
$$a_i+a_j=a_k$$

$Sumtriples1(a_1,...,a_n:R)$
	for i:=1 to n
		for j:=1 to n
			for k:=1 to n
				if $a_i+a_j=a_k$ then return true
	return false

$runtime: O(n^3)$

Let's improve it

First:
for k:=1 to n
	if $a_i+a_j=a_k$ then
		return true
is just a linear search, which is O(n) that can become O(logn) if we sort it and use Binary search instead.

Secondly:
for i:=1 to n
	for j:=1 to n
is redundant, since half of it is repeated, so we only need to for j to go from i to n instead of 1 to n.

In total, this reduces everything to $O(n^2log(n))$, which is better than $O(n^3)$

