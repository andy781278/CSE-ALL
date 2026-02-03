
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

