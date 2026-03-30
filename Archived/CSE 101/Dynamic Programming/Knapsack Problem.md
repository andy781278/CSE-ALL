You are a burglar with a knapsack that can hold weight C. There is a hash table of weight/value pairs for items, get maximum value.

BTKS(w[1..n],v[1..n],C)
	(Base Cases)
	If:
		C=0 return 0
		n=0 return 0
		w[n]>C return BTKS(w[1..n],v[1..n],C)
	IN = BTKS(w[1..n],v[1..n],C-w[n])+V[n]
	OUT = BTKS(w[1..n-1],v[1..n-1],C)
	return max(IN,OUT)

Total number of different recursive calls: (n+1)(C+1)
- there are up to n+1 different items to take from, and the knapsack can take C+1 different items

Recursion:
- How to calculate KS[j,b]
	- OUT: so if item j is not included in the backpack
		- KS[j,b]=KS[j-1,b]
	- IN: if item j is in backpack
		- KS[j,b]=KS[j,b-w[j]]+v[j]
Since we don't know which is bigger, compute both and take max

Ordering subproblems
- There's two dimensions now j and b, one for each argument, so you can't go 0..n anymore
- Instead, build a mind map and go back to [j-1,b] and [j,b-w[j]] from [j,b]
- order the problems by filling in each row from left to right and from top to down

Final Output
- KS[n,C]

```
function Knapsack(w,v,C)
	KS[j,0]=0 for all j
	KS[0,b]=0 for all b
	for j from 1 to n
		for b from 1 to c
			if w[j]>b:
				KS[j,b]=KS[j-1,b]
			else:
				IN = v[j]+KS[j,b-w[j]]
				OUT = KS[j-1,b]
				KS[j,b]=max(IN,OUT)
	return K[n,C]
```
### Runtime
O(nC)

