#Algorithm #DivideAndConquer
Note: O(n) for addition

Given a and b, both n digits, multiply them, what is the runtime?

you multiply each of the digits in b by whole of a, which is $n^2$ operations
then you add them, which is n-1 operations
in total, $O(n^2)$

Too slow, lets do divide and conquer
![[Screen Shot 2025-11-17 at 1.09.35 PM.png]]

Function Multiply(2 n digit integers of x and y): outputs xy
	if n=1: return x*y
	split x into $x_l, x_r$, and split y into $y_l,y_r$
	Foil:
		$P_1 = multiply(x_l,y_l)$
		$P_2 = multiply(x_r,y_l)$
		$P_3 = multiply(x_l,y_r)$
		$P_4 = multiply(x_r,y_r)$
	return $P_1 * 10^n + (P_2 + P_3)*10^{n/2} + P_4$
Master Theorem: $T(n) = 4T(n/2)+O(n)$
$a=4,b=2,d=1, a>b^d. T(n) = O(n^{log_2 4}) = O(n^2)$

Function Karatsuba Multiplication(2 n digit integers of x and y): outputs xy
	if n=1: return x*y
	split x into $x_l, x_r$, and split y into $y_l,y_r$
	Foil:
		$R_1 = multiply(x_l,y_l)$
		$R_2 = multiply(x_r,y_r)$
		$R_3 = multiply((x_l+x_r)(y_l+y_r))$
	return $R_1 * 10^n + (R_3 - R_1 - R_2)*10^{n/2} + R_2$
Master Theorem: $T(n) = 3T(n/2)+O(n)$
$a=3,b=2,d=1, a>b^d. T(n) = O(n^{log_2 3}) = O(n^{1.58...})$


