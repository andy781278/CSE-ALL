Instance: $[(s_1,f_1,v_1),...,(s_n,f_n,v_n)]$
Solution: subset of events S
Constraints: no two events in S overlap
Objective: $\sum_{i\in S} v_i$
Goal: Maximize

- Sort events by endtime
- pick last to end, $I_n$, not necessarily good to include
- we'll try both possibilities
	- Case 1: we exclude $I_n$
		- Recurse on $[I_1,...,I_{n-1}]$
	- Case 2: we include $I_n$
		- Recurse on set of all intervals that do not conflict with $I_n$

```
BTWES(I1,...,In): //sorted by endtimes
	if n=0 return 0
	if n=1 return v1
	Out = BTWES(I1,...,In-1)
	let Ik be last event to end before In starts
	In = BTWES(I1,...,Ik)+vn
	return max(Out,In)
```

Worst Case: $T(n)=2T(n-1)+O(n) \rightarrow O(2^n)$

We can make this easier with Dynamic Programming.
By storing previous calculated outputs from recursion, we can save time and prevent recalculation by just reusing what we calculated before

[[Weighted Event Scheduling with Dynamic Programming]]