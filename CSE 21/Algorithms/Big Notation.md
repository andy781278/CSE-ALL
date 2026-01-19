#Algorithm
### $f(n) \in \Theta (g(n))$
- $\lim_{n \rightarrow \infty} \frac{f(n)}{g(n)} = c$ where 0 < |c| < $\infty$
- f and g scale the same way, like wc times for bubble sort and min sort
- output is just as fast as input
### $f(n) \in o(g(n))$
- $\lim_{n \rightarrow \infty} \frac{f(n)}{g(n)} = c$ where c = 0
- f scales better than g, like binary search and linear search time
- output is strictly faster than input
### $f(n) \in \Omega (g(n))$
- $\lim_{n \rightarrow \infty} \frac{f(n)}{g(n)} = c$ where 0 < |c|
- f scales the same or worse than g
- output is no faster than input
### $f(n) \in O(g(n))$
- $\lim_{n \rightarrow \infty} \frac{f(n)}{g(n)} = c$ where 0 <= |c| < $\infty$
- $O(g(n)) = \Theta(g(n)) || o(g(n))$
- f scales the same or better than g
- output grows no slower than input
- means that there are constants c and k such that  $f(n) \leq Cg(n)$ for all $n \geq k$
- How to determine/prove Big-O between 2 expressions?
	1. Look for C and k directly
	2. Use Properties
		- Domination - If $f(n) \leq g(n)$ for all n then $f(n) \in O(g(n))$
		- Transitivity - if $f(n) \leq g(n)$ and $g(n) \leq h(n)$ then $f(n) \leq h(n)$
		- Additivity - if $f(n) \leq g(n)$ and $h(n)$ is non-negative then $f(n) + h(n) \in O(g(n) + h(n))$
		- Multiplicativity - if $f(n) \leq g(n)$ and $h(n)$ is non-negative then $f(n) * h(n) \in O(g(n) * h(n))$
		- Sum is maximum - If $f(n) + g(n) \in O(max(f(n),g(n)))$ (does not work if there isn't a fixed number of terms, like a sum of series)
		- Ignoring constants - For any constant c, $c*f(n) \in O(f(n))$

