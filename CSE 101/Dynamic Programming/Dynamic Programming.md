---
aliases:
  - DP
---
programming paradigm that stores previous calculated outputs from recursion, we can save time and prevent recalculation by just reusing what we calculated before

#### Although it is being called Dynamic Programming, these problems resemble more of an Exhaustive Recursive Search

1. Define sub-problems and corresponding array
2. What are the base cases
3. Give recursion for sub-problems (case analysis)
4. Order the subproblems, find the bottom-up order
5. What is the final output
6. Make the algorithm, put it all together
7. Correctness Proof
8. Runtime Analysis

- Every DP problem can be represented with a DAG and solved with a graph and finding minimum/maximum path (Topological Ordering)
	- the vertex is the smallest iteration of a sub-problem
	- the edges are the dependencies between vertices

![[Weighted Event Scheduling with Dynamic Programming]]