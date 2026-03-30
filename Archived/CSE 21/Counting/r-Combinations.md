#Counting
Set S with n elements, get subset of k different elements of S, order doesn't matter
[[Binomial Coefficient]]: $\binom{n}{k}$
Also counts:
- number of binary strings with length n and has k *1*s
- selecting k positions in n ordered items

Useful Formula/Identity:
Symmetry of Pascal's Triangle
$$\binom{n}{k}=\binom{n}{n-k}$$
(Pascal's Identity)
$$\binom{n+1}{k}=\binom{n}{k-1}+\binom{n}{k}$$
[[Sum Identity]]
$$\sum_{k=0}^{n}\binom{n}{k}=2^n$$

n choose k, C(n,k), nCk, ( n k )

you can turn C to P by multiplying by k!
since we got the P here, lets do C
P(n,r) = nPr = n(n-1)(n-2)...(n-r+1) = $n! / (n-r)!$ 
$n!/(n-r)! / r! = n!/(k!(n-k)!)$

