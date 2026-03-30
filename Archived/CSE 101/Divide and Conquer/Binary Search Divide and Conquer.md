You already know what binary search is:

![[Binary Search]]

Recurrence relation of runtime for this thingy:
$$T(n)=T(n/2)+O(1)$$

You get a constant time with in-place recursion implementation
take two pointers i and j, find midpoint m, compare m to the element you want, and move i or j depending on if the element is less or more than m. You stop when m=what you want

But this is not all. There are a series of problems that can be solved by processes similar to binary search.

### Two Runners
runner A start at 0, runner B start at x. runner A wins at n seconds. Find j which is the position when A passes B. A[j]<=B[j] and A[j+1]>B[j+1]

We know such position exists because of IVP, there has to be a turning point in order for A to win, since B got a head start of x. There might be multiple positions like that since A and B can overtake each other constantly
```
if n=1, return 0
assign m=n/2
compare A[m],B[m]:
	if A[m]<= B[m] and A[m+1]>B[m+1] return m
	If A[m] > B[m], recurse on list A[0...m] and B[0...m]
	If A[m+1]<= B[m+1], recurse on A[m+1...n] and B[m+1...n]
```
Explanation: low is 0, high is n. While low+1 < high, we find middle m, and if that middle is the right thing, then return that, else let high be m if m is too late, and let low be m+1 if m is too early

This will be O(logn)

### Correctness
Loop invariant:
After every iteration, A[lo] <= B[lo] and A[hi] > B[hi]

Proof
- Base case: before loop, A[0] <= B[0] and A[n]>B[n] by parameters
- suppose that after t iterations, A[lo] <= B[lo] and A[hi] > B[hi]
- then after the next iteration
	- A[m] <= B[m] and A[m+1] > B[m+1] and algorithm terminates with correct index
	- A[m] > B[m]
		- Then algorithm sets hi = m, by IH, A[lo] <= B[lo] and after reassignment of hi, A[hi] > B[hi]
	- A[m+1] <= B[m+1]
		- Then alg sets lo=m+1, by IH, A[hi]>B[hi] and after reassignment of lo, A[lo] <= B[lo]
- When algorithm terminates, it does it only when lo+1=hi, that means lo and hi are next to each other, and that A[lo] <+ B[lo] and A[lo+1] > B[lo+1]