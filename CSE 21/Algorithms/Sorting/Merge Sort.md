#Sorting #Algorithm #DivideAndConquer 

### HOW
Divide and Conquer:
Divide the list into 2 sub-lists
Recursively sort each sublist
Conquer by merging the two sorted lists into a single list

MergeSort($a_1,...,a_n$):
if n = 0:
	return nothing
if n =1
	return $a_1$
m = n/2
$L_1$ = MergeSort($a_1$ to $a_m$)
$L_2$ = MergeSort($a_{m+1}$ to $a_n$)
return RMerge($L_1,L_2$)

RMerge(list 1, list 2): (size k, size l)
if nothing in list 1: return list 2
if nothing in list 2: return list 1
if e1 from list 1 < e2 from list 2: return e1 * RMerge(list 1 sans e1, list 2)
else: return e2 * RMerge(list 1, list 2 sans e2)

### WHAT

### WHY

#### Prove RMerge
Regular Induction:
Base Case k+l = 0, then the alg returns nothing which is trivially sorted
Inductive Hypothesis: k+l = n for any n $\in \mathbb{R}^+$, Assume RMerge works for any two lists with the combined size of n-1. Consider two lists $[a_1,a_2,...,a_k]$ and $[b_1,b_2,...,b_l]$ such that k+l=n
Inductive Step: 
Case k=0 (list 1 empty): then alg returns list 2, which is sorted by ind hyp
Case l=0, same thing
Case k>0, l>0, $a_1<b_1$: $a_1$ is less than all other elements, and RMerge($[a_2,a_3,...,a_k]$,$[b_1,b_2,...,b_l]$) is sorted by hypothesis, so $a_1 \circ$RMerge($[a_2,a_3,...,a_k]$,$[b_1,b_2,...,b_l]$) is a sorted list of all elements
Case $b_1 \leq a_1$: $b_1$ is less than all other elements and RMerge($[a_1,a_2,...,a_k]$,$[b_2,b_3,...,b_l]$) is sorted by hypothesis, so $b_1 \circ$RMerge($[a_2,a_3,...,a_k]$,$[b_1,b_2,...,b_l]$) is a sorted list of all elements

#### Prove MergeSort
Base Case: n=0 -> return empty list which is trivially sorted. n=1 -> return a list with only $a_1$ which is trivially sorted
Induction Step: Suppose n>1, assume, as the **Strong Induction Hypothesis**, that MergeSort successfully sorts all lists with k elements, for any 0 $\leq$ k < n
Prove MergeSort(list with n elements) returns a list with all n elements

Since n>1, we can set m = n/2
$L_1$ = MergeSort($a_1,...,a_m$), since size of $a_1$ to $a_m$ < n, $L_1$ is a sorted list of $a_1,...,a_m$
$L_2$ = MergeSort($a_{m+1},...,a_n$), since size of $a_{m+1}$ to $a_n$ < n, $L_2$ is a sorted list of $a_{m+1},...,a_n$

By correctness of RMerge, RMerge($L_1,L_2$) is a sorted list of all n elements

### WHEN

T(n) = 2T(n/2) + O(n)

2 : number of recursive calls
n/2: size of recursive calls
O(n) : runtime of the non-recursive part

![[Master Theorem]]

Using the master theorem, a=2, b=2, d=1, $2 = 2^1$, so $O(n^1 log(n))$
