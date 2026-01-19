#Algorithm 

How many 2x1 domino tilings are there in a 2xn space?
Let DT(n) be the number of domino tilings in a 2xn space

| DT(1) | DT(2) | DT(3) | DT(4) | DT(5) |
| ----- | ----- | ----- | ----- | ----- |
| 1     | 2     | 3     | 5     | 8     |
All domino tilings = start with 1 vert + start with 2 hor
start with vertical = DT(n-1)
start with horizontals = DT(n-2)
DT(n) = DT(n-1)+DT(n-2) for all n>2
DT(1) = 1, DT(2) = 2

Using HRRCC, we guess $DT(n) = Ar^n$
DT(n)=DT(n-1)+DT(n-2)
$Ar^n = Ar^{n-1}+Ar^{n-2}$
$r^2 = r+1$
$r^2-r+1=0$
$r=\frac{1+\sqrt{5}}{2}, \frac{1-\sqrt{5}}{2}$
r = $\varphi, \overline \varphi$
$DT(n)=A\varphi^n  + B \overline \varphi^n$
Thus $DT(n) = \theta(\varphi^n)$

