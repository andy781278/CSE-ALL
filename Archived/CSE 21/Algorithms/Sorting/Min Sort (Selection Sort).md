#Algorithm #Sorting 

### WHAT
Given a list $[a_1,a_2,...,a_n]$
- for each element in the list (i from 1 to n):
	- Find the smallest element ($x_i$) in list
		- Go through the list, compare an arbitrary smallest so far to each element
	- swap $x_i$ with the smallest element
### WHEN
How many swaps for
- Best case: 0
- Worst case: n-1 (cyclically shifted by 1)
How many comparisons for
- BC/WC (they're the same amt): $1+2+3+4+...+(n-1) = \frac{n(n-1)}{2}$
### WHY
1. [[Loop Invariant]]
	After t iterations,
	1. the first t elements are in sorted order
	2. the first t elements are the smallest
2. How can we show that this loop invariant is true?
	Base case: after 0 iterations:
		The first 0 elements are in sorted order (vacuously true)
		The first 0 elements are the smallest (vacuously true)
	Inductive Hypothesis: Suppose the loop invariant is true after t iterations for t $\geq$ 0
		Show that it is true after t+1 iterations
		During the (t+1) iteration, algo finds $a_m$, the minimum of $a_{t+1},...,a_n$, then we swap $a_m$ with $a_{t+1}$. So after (t+1) iterations, $a_{t+1}$ is the minimum value of $a_{t+1},...,a_n$.
3. Once we do, why can we conclude that the program is correct?
	Therefore: for any $0\leq t\leq n-1$, 
	This particular algorithm states that the loop invariant is true after n-1 iterations, so after the program terminates
		1. the first n-1 elements are in sorted order
		2. the first n-1 elements are the smallest
	The last element $a_n$ is greater than all elements to its left. This is why we conclude that this list is sorted.