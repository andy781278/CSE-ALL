#Algorithm

Pairs of elements from a set of size n:
P(1) = 0, for n>=2, P(n) = P(n-1)+n-1

Can't use HRRCC, not homogeneous, since it adds n-1, instead of multiplying the P(n-1) or smth
Then we have some options:
- guess and check
- Unravel
- Characteristic Polynomial

P(n) = n(n-1)/2

Guess and Check: Induction
P(1) = 1(0)/2 = 0
P(k)=k(k-1)/2, try to get k(k+1)/2
P(k+1)=P(k)+k+1-1 = k(k-1)/2 + k = k(k-1)+2k/2 = k(k+1)/2

