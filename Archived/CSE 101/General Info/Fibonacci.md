$$F_n = F_{n-1}+F_{n-2}$$ for $n \geq 2$, $F_0=1,F_1=1$


How fast does this grow?
Seems like it is always a little less than doubling every time
$F_n \leq 2F_{n-1}$

Using Characteristic Polynomial, $F_n=r^n$, we can simplify it to find $r=1.618, F_n= \Theta (1.618^n)$

Let's make an obvious algorithm  for Fibonacci

```python
func Fib1(n):
	if n==0:
		return 0
	if n==1:
		return 1
	return fib1(n-1)+fib1(n-2)
```

This is bad because the same problem is done over and over
Let's make it faster

Let's make a methodical algorithm for fibonacci

```python
func Fib2(n):
	Create array fib[0..n-1]
	fib[0]=1
	fib[1]=1
	for i=2 to n:
		fib[i]=fib[i-1]+fib[i-2]
	return fib[n-1]
```

This is $O(n)$, but actually $O(n^2)$ because the number goes exponentially bigger, because you need to add.
- If we add two numbers that fit in word size, then this is O(1)
	- Floating point same thing
- But if we add two n bit numbers and get an exact answer, where n is larger than word size, then we need to perform addition in software, which makes it O(n). 

|            | Float | n<word size | arbitrary n |
| ---------- | ----- | ----------- | ----------- |
| Add        | O(1)  | O(1)        | O(n)        |
| Sub        | O(1)  |             |             |
| Comparison | O(1)  |             |             |
| Mult       | O(1)  |             |             |

Approximate how many bits Fib(n) takes in general?
Fib(50) = 12,...,...,... -> ~33 to 34 bits, ~0.694n bits, number of bits grows linearly

