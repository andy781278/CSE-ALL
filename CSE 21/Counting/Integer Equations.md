#Counting
consider $a+b+c+d=10$ where a,b,c,d are non-negative integers, how many sol for eq?
consider each var a castle, and the constant the num of knights
therefore $\binom{10+4-1}{4-1}$
Differnt senario:
for general equation, $a_1+a_2+...+a_k = n$, where n and $a_i$ have to be **positive** ints
Now we have to make sure each var has at least 1
for each $1\leq a_i \leq n$, let $x_i = a_i -1$, that converts the og eq to $x_1+x_2+...=n-k$  where $n-k$ and $x_i$'s are non-negative
There are $C((n-k)+k-1,k-1) = C(n-1,k-1)$ solutions
