This is solved with DP

1. Subproblem

Let dist(v) be shortest dist from s to v

2. Base Case

dist(s)=0

3. Recursion

Think about what an example vertex J needs in order to know dist(J), we need to know its incoming neighbors' weights

dist(x)=min{dist(v)+l(v,x)} for all neighbors v of x

4. Ordering

Topological ordering of vertices

Runtime
O(|V|+|E|)