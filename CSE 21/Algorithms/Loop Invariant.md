#Algorithm

A Loop Invariant is a property that remains true after each time the body of a loop is executed.
OR
What you can say about the algorithm after t loops

This is useful to prove the usefulness of **iterative** algorithms, no recursive algorithms yet.

Steps to prove 
1. Look for loop invariants
	State the property precisely
2. Prove that it is an invariant
	- it must be true after **any number** of loops
	- Induction Variable (t): The number of times through the loop.
	- Base case: Need to show the statements holds for t=0, before any loops start
	- Induction step:
		- Induction Hypothesis: Suppose the statement holds true after t loops
		- Need to show the statement holds after t+1 loops
3. Use the invariant to prove correctness
	Show that when the loop is finished, the invariant guarantees that we've reached a solution.
