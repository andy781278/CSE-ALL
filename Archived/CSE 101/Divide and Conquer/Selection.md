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
if we can choose the median as the pivot every time, we can minimize the process and get:
$$T(n)=T(n/2)+O(n) = O(n)$$
If we get lucky, we can solve it in O(n) time.

If we're unlucky, we'll pick either the biggest or smallest element every time.
Then it is:
$$T(n)=T(n-1)+O(n)$$
which is unsolvable by master theorem, but we can still solve it by unraveling, which gives you $T(n)=O(n^2)$

So is it worth it to use this algorithm even if there's a chance of it being slower than sorting? Let's find the expected runtime

- we split the runtime between if we get the pivot in the inner 50% of the list or the outer 50%. The inner will run <= 3n/4, and the outer will run n.
- $ET(n)\leq \frac{1}{2}ET(\frac{3n}{4})+\frac{1}{2}ET(n)+O(n)$
- $ET(n)\leq ET(\frac{3n}{4})+O(n)$
- $ET(n)\leq O(n)$

So in practice, $O(n)$ is probably a lot more likely to happen than $O(n^2)$

But this is still random, so it is not deterministic, and computer scientists don't like that. They made a better one. They used recursive calls to find an element that's roughly close to the median, and they use that as the pivot.

### Median of Medians
```
function MoM(L,k):
	if size(L)<10:
		sort L and return kth element
	Partition L into sublists S[i] of 5 elements each
	for i=1,...,n/5:
		m[i]=MoM(S[i],3) //pos 3 is median of a list of 5 elements
	M = MoM([m[1],...,m[n/5]],n/10) // n/10 is the median of medians
	
	QuickSelect but call MoM instead of itself.
```
This process is deterministic, no randomness used.
3n/10 <= M <= 7n/10

$T(n)=T(n/5)+T(7n/10)+O(n)$
this devolves into linear time.