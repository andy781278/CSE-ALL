
When multiplying normally, time takes $O(n^2)$ because we have to multiply n^2 amount, then add n-1 amount


can we make it better? Let's use Divide and Conquer


Let's split each number into its left and right halves which are each n/2 bits long
example, split 12345678 into 12340000 and 5678

![[Pasted image 20260217210417.png]]

### multiply
```
function multiply(n bit x,y):
	if n=1: return xy
	xl,xr and yl,yr be the left-most and right-most n/2 bits of x and y
	p1=multiply(xl,yl)
	p2=multiply(xl,yr)
	p3=multiply(xr,yl)
	p4=multiply(xr,yr)
	return p1 * 2^n + (p2 + p3) * 2^(n/2) + p4
```

### Runtime
T(n) be the multiply algorithm runtime
Then $T(n)=4T(\frac{n}{2})+O(n)$



### multiplyKS
```
function multiplyKS(x,y):
	if n=1: return xy
	xl,xr and yl,yr be the left-most and right-most n/2 bits of x and y
	r1 = multiplyKS(xl,yl)
	r2 = multiplyKS(xr,yr)
	r3 = multiplyKS((xl+xr)(yl+yr))
	return r1*2^n + (r3-r1-r2) * 2^(n/2) + r2 
```

### Runtime
$T_{KS}(n)$ be the multiply algorithm runtime
Then $T_{KS}(n)=3T_{KS}(\frac{n}{2})+O(n)$

Using master theorem, we can see the big O notation of these two algorithms multiply and multiplyKS:

$T(n) \in O(n^2)$
$T_{KS}(n)\in O(n^{1.585})$


Improve it more?

We can use a trinomial, which splits into 9 recursions, we can reduce it down to 5 with some matrix algebra, which results in 
$O(n^{1.4})$

Improve it more?

turns out, you can split it up into k equally sized parts, and combine them with 2k-1 mults, so that gets you
![[Pasted image 20260217213148.png]]

which approaches 1 as k approaches infinity

But we use k=3 because the linear add increases in size quadratically as k increases.

This is called the $Cook-Toom_k$ algorithm