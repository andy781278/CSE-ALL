#Algorithm
#DivideAndConquer
Theorem: If $T(n) = aT(n/b) + O(n^d)$ for some a>0, b>1, D>=0, then

$$T(n) \in \left\{ \begin{array}{rcl} O(n^d) & if & a<b^d \\O(n^dlog(n)) &if&a=b^d\\ O(n^{log_b a})&if&a>b^d \end{array}\right.$$
