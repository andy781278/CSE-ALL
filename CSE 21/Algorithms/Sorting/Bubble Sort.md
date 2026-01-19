#Algorithm #Sorting 

### WHAT
Given a list $[a_1,a_2,...,a_n]$
- For each element $a_1$ to $a_n$, named $a_i$
	- sorted = true
	- For each element $a_1$ to $a_n$ named $a_j$
		- if $a_j>a_i$
			- swap them
			- sorted = false
	- if sorted
		- exit

### WHEN
Swaps
- BC: 0
- WC: (n-1)+(n-2)+...+2+1 = $\frac{n(n-1)}{2}$
Comparisons
- BC: n-1
- WC: $\frac{n(n-1)}{2}$