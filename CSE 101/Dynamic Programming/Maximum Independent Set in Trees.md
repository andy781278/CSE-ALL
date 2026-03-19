find a set of vertices from a tree such that no two vertices in there are connected and they have the maximum sum together

1. subproblems

Let M[k] = (IN,OUT) where IN is the weight of the maximal independent set of the subtree hanging from k including k and OUT is excluding k

2. base cases

if v is a leaf then M[v]=(w(v),0)

3. recursion

In order to compute M[k], what do we need to know? The subtree of k, IN and OUT

Imagine k has 2 children, c1 and c2
$IN_k = w(k)+\sum_c OUT(children)$
$OUT_k=\sum_cMAX(IN_c,OUT_c)$

4. ordering

order by layers, start from bottom with the leaves and work to the root

5. Output

$MAX(IN_r,OUT_r)$

