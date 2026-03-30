---
aliases:
---
given a string of letters, how to separate words?

- Define the array values (subproblems)
	- Let S(k) be true if x[1..k] is a valid seq of words and false otherwise
- Base Cases
	- S(0) = true
- Give recursion for sub-problems
	- S(k) is true iff there exists some j between 1 and k such that 
		- S(j-1) is true
		- x[j..k] is a word
- Order the problems
	- 0,..,n
- Output
	- S(n)

```
function StringReconstruction(x[1..n]):
	Init S to be flase for all and prev to be null
	S(0)=true
	for k from 1 to n:
		j=k-1
		while(not S(k) and j>0):
			if S(j) and x[j+1..k] is valid word
				S(k)=true
				prev(k)=j
			else
				j--
	if S(n)
		p=n
		while p>0 print; p=prev(p)
```

### Runtime
O(n)