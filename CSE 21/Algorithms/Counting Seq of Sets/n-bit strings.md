#Algorithm #DivideAndConquer 
bit strings can only have 0s or 1s.
n-bit strings are bit strings of size n

Let BS(n) be the number of n bit strings
Count the set of n-bit strings by separating them
all n-bit strings = start with 0 + start with 1

BS(n) = 2BS(n-1)
BS(0) = 1

Unraveling:
1 BS(n) = 2BS(n-1)
2 BS(n) = 2(2BS(n-2)) = 4BS(n-2)
3 BS(n) = 2(4BS(n-3)) = 8BS(n-3)
k BS(n) = $2^kBS(n-k)$
n BS(n) = $2^nBS(n-n) = 2^n$ 


### n-bit strings avoid substring 11
Let A(n) be the number of n-bit 11 avoiders
A(0) = 1
A(1) = 2
A(2) = 3
A(3) = 5
Perhaps fib, so we set it as such
all nbit 11 avoiders = start with 0 + start with 1 (10)
A(n) = A(n-1) + A(n-2)

### n-bit strings avoid substring 111
A(0)=1 1
A(1)=2 0 1
A(2)=4 10 01 11 00
A(3)=7 000 001 010 100 011 101 110
Start with 0: A(n-1)
0 _ _ _ _ _ _ (n-1)
Start with 1: B(n-2)+B(n-3)
1 0 _ _ _ _
1 1 0 _ _ _ _
B(n) = B(n-1)+B(n-2)+B(n-3)
guess that B(n)=A$r^n$
$r^3=r^2+r+1$
$r^3-r^2-r-1=0$
$r_1=1.8393, r_2 = -0.4-0.6i, r_3 = -0.4+0.6i$
B(n) = $\Theta(1.8393...^n)$
