#Proof
[[Bijection Proof]]
1. find a set counted by the LHS
2. find a set countd by the RHS
3. build a bijection between these two sets
Example
$\binom{n}{k} = \binom{n}{n-k}$
4. the set of all binary strings with length n and k 1s
5. the set of all binary strings with length n and n=k 1s
6. consider that the map that changes all 1s into 0s and all 0s into 1s, it is a bijection between two sets above

[[Same-Set Proof]]
1. Find a set <- define this first clearly (Let S be the set...)
2. explain why the LHS counts this set <- do 2 and 3 separately, no moving terms in between
3. explain why the RHS counts this set
Example
$\sum_{k=0}^{n} \binom{n}{k} = 2^n$
4. Let S be a set of all binary strings length n
5. $2^n$ counts the number of binary strings length n
6. We compute the Summation, creating a partition of many subsets added together. For example, all n length strings with k=0 ones, k=1 ones,..., k=n ones. This accounts for all n length strings
Problem
$\sum_{k=0}^{n} k \binom{n}{k} = n2^{n=-1}$
7. Let n be number of students, and set S be the set of all study groups formed by these n students, 1 of them has to be a leader
8. LHS: size of study group is k, so k ranges from 0 to n, next, pick k people from all n students (n choose k), finally, pick 1 leader from this study group (k)
9. RHS: pick leader from n students (n), then, pick a subset of remaining students, they are non-leader group membets ($2^{n-1}$)