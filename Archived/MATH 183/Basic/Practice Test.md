1. T/F
	1. T
	2. T
	3. F
	4. F

2. ABCD
	1. B
	2. B,D
	3. C
	4. D
	5. C

3. Draw
	1. B

4. COVID
A = have covid = 0.1
Ac = dont have covid = 0.9
B = tests positive = P(B|A)P(A)+P(B|Ac)P(Ac)
Bc = tests negative = 1-P(B)

0.95 -> P(B|A)
0.1 -> P(B|Ac)
0.1 -> P(A)

$P(A|B)=\frac{P(B|A)P(A)}{P(B|A)P(A)+P(B|A^c)P(A^c)}$
P(B)=0.185
P(Bc)=0.815

$P(A|B)=\frac{0.95*0.1}{0.95*0.1+0.1*0.05}$
P(A|B)=0.51

$P(A^c|B^c)=\frac{P(B^c | A^c)P(A^c)}{P(B^c)}$
$P(A^c|B^c)=\frac{0.9*0.9}{0.815}$
$P(A^c|B^c)=0.994$

$P(A|B_1 \cap B_2) = \frac{P(B_1 \cap B_2 | A)P(A)}{P(B_1 \cap B_2)}$
$P(A|B_1 \cap B_2) = \frac{P(B_1 \cap B_2 | A)P(A)}{P(B_1 \cap B_2 | A)P(A)+P(B_1 \cap B_2 | A^c)P(A^c)}$
$P(A|B_1 \cap B_2) = \frac{0.95^2 * 0.1}{0.95^2 * 0.1+0.1^2 * 0.9}$

5. 
	1. $C=\frac{1}{b-a}$
	2. Uniform Distribution on [a,b]
$$ CDF: f_X(x)=\begin{cases} 
0 & x < a \\
\frac{x-a}{b-a} & a \leq x \leq b \\
1 & x > b
\end{cases} $$
