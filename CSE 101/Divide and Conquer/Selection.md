algorithm takes in a list of numbers length n and integer 1<=k<=n and output kth smallest element in the list

Normal method: sort list and output kth element, O(nlog(n))

can we do better?

Divide and Conquer

- Split the list using a random pivot
- list => list of elements greater than pivot + list of elements smaller than pivot
- Given list $L = [a_1,...,a_n]$, pivot $a_i$, rearrange list L so elements smaller than $a_i$ are to the left, bigger are to the right

### QuickSelect
```
procedure QuickSelect(a[1...n],k):
	if n==1:
		return a[1]
	pick random int in a called v
	split list into sets SL, Sc, SR (SL<v, Sc=v, SR>v)
	if k <= |SL|:
		return QuickSelect(SL,k)
	if k <= |SL|+|Sv|:
		return v
	else:
		return QuickSelect(SR,k - |SL| - |Sv|)
``` 

### Runtime
$$T(n) \leq max(T(L),T(R)) + cn$$