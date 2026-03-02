![[Weighted Event Scheduling]]

only n+1 out of the $2^n$ recursive calls are distinct.

```
WESDP(I1,...,In): //sorted by endtimes
	A[0]=0
	for k=1...n:
		j=1
		while End(Ij) <= Start(Ik):
			j++
		In = vk+A[j-1]
		Out = A[i-1]
		A[k]=max(In,Out)
	return A[n]
```

9. Define sub-problems and corresponding array
	- (subproblems are often restatements of the original problem)
	- OG: Find max val among (I1,...,In)
	- Sub: Let A[k] be amx among (I1...,Ik)
10. What are the base cases
	- true for any input
	- A[0]=0
11. Give recursion for sub-problems (case analysis)
	- (break up subproblem into distinct cases)
	- A[k]=...
		- Case 1: Ik is not a part of max val schedule
			- A[k]=A[k-1]
		- Case 2: Ik is
			- A[k]=vk+A[j-1]
			- where j-1 is the last event to end before k starts
	- A[k] is the max between the two cases
12. Order the subproblems, find the bottom-up order
	- since each subproblem is dependent on subproblems of smaller index, we can order subproblems from 0 up to n
13. What is the final output
	- A[n]
14. Put it all together into iterative alg that fills the array step by step
![[Pasted image 20260302000459.png]]
15. Correctness proof
![[Pasted image 20260302000549.png]]
16. Runtime Analysis
- $O(n^2)$

