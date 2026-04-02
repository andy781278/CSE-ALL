Let X be the space in which data lie:
A distance function $d: X\times X \rightarrow \mathbb{R}$ is a **metric** if it satisfies the following properties:
- Nonnegativity: $d(x,y)\geq 0$
- Identity of indiscernibles: $d(x,y)=0 \;\text{iff}\; x=y$
- Symmetry: $d(x,y)=d(y,x)$
- Triangle inequality: $d(x,z) \leq d(x,y) + d(y,z)$


##### Examples
X=$\mathbb{R}$ and $d(x,y) = |x-y|_p$  (DO THIS)
check:
- Nonnegativity: $d(x,y)\geq 0$
	- since X is in 1D, m=1
	- take this formula: $|x-x|_p = (\sum_{i=1}^{m} |x_i-z_i|^p)^{\frac{1}{p}}$
	- if m=1, then $|x-x|_p = (\sum_{i=1}^{1} |x_i-z_i|^p)^{\frac{1}{p}}$
	- which is $|x-x|_p = |x_i-z_i|$
	- the absolute function makes it always non-negative
- Identity of indiscernibles: $d(x,y)=0 \;\text{iff}\; x=y$
	- if x != y then their difference must be >0.
- Symmetry: $d(x,y)=d(y,x)$
	- because of abs, |x-y| = |y-x|
- Triangle inequality: $d(x,z) \leq d(x,y) + d(y,z)$
	- since everything is absolute, 2 addition would be more than 1 addition unless if it was 0. But in the case that d(x,y) or d(y,z) is 0, then that would be x=y or y=z, or both. In all of those scenarios, either x=z which means its the smallest possible value, or it's something else, in which case xy and yz has to be more or 0 which would make it all 0.

X={strings over some alphabet} and d = edit distance
Check:
- Nonnegativity: $d(x,y)\geq 0$
	- identical data points with no edit is distance 0, and you can only add to distance with edits, so you can't go below 0.
- Identity of indiscernibles: $d(x,y)=0 \;\text{iff}\; x=y$
	- If the strings are the same, then you don't need edits, therefore distance would be 0, therefore they are equal.
	- If they are not equal, then you need editing to make them equal, which would make distance > 0.
- Symmetry: $d(x,y)=d(y,x)$
	- If you have a sequence of operations to get from data A to data B, then reversing that sequence would get you from data B to dat A. The reverse of a sequence does not change its length.
- Triangle inequality: $d(x,z) \leq d(x,y) + d(y,z)$
	- if you imagine 3 data points xyz, separated by distances d(x,y), d(y,z), and d(x,z).
		- Then anything you do to make x into y you can also do to make it into z, but y still needs to reach z.
		- In a case where d(x,y) is minimized so 0, and d(y,z) is huge, like 10k, then d(x,z) is 10k as well, since in the minimum scenario, they're still equal, so it's fine.

What about a distance function that don't suffice for metric?
Let q,p be some probability distribution on set X
The **Kullback-Leibler divergence** or **relative entropy** between p and q is:
$d(p,q)=\sum_{x\in X}p(x)log \frac{p(x)}{q(x)}$
- It's not a metric, because it violates symmetery
	- $\sum_{x\in X}p(x)log \frac{p(x)}{q(x)} \neq \sum_{x\in X}q(x)log \frac{q(x)}{p(x)}$

