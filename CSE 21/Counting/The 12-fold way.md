#Counting
organization of what has been taught so far

All we've been doing is learning how to create a function f: X -> Y
We have access to the X which is the balls, and Y which is the boxes, but the arrows between them we have to draw

There are n balls and x boxes
n letters in the alphabet and x spaces
n knights and x castles

Any f -> $n < x, n=x, n > x$
Doesn't matter: x can map to y or it could not, y could have x connected or it could not, doesn't matter, not specified. However, I do think that it is expected that all of the x connects to something at least, bc these problems concern putting balls into boxes, the minimum requirement is that at least 1 ball goes in 1 box, or at least 1 x links to 1 y

[[Injective]] -> $n\leq x$: how many ways without repeating x
One-to-one: Each y in Y can only have 1 x in X pointed to it, no two x in X can point to the same Y
each box can only have max 1 ball in it, meaning number of balls has to be less or equal to number of boxes

[[Surjective]] -> $x \leq n$: used at least once
Onto: Each y in Y has to have at least 1 x in X pointed to it, no y in Y is isolated/unconnected
each box has to have at least 1 ball in it, meaning number of balls has to be at least equal or bigger than the number of boxes

For $F: N \rightarrow X$

| Elements of N (balls) | Elements of X (boxes) | Any f                                      | f [[Injective]] (one-to-one)         | f [[Surjective]] (onto)                                                               |
| --------------------- | --------------------- | ------------------------------------------ | ------------------------------------ | ------------------------------------------------------------------------------------- |
| Distinguishable       | Distinguishable       | $x^n$ <- [[Power Rule]]                    | P(x,n) <- [[r-Permutations]]         | $\sum_{k=0}^{x}\binom{x}{k}(x-k)^n(-1)^k$ <- [[Each character is used at least once]] |
| Indist.               | Dist.                 | $\binom{n+x-1}{x-1}$ <- [[Stars and Bars]] | $\binom{x}{n}$ <- [[r-Combinations]] | $\binom{n-1}{x-1}$ <- [[Integer Equations]]                                           |
| Dist.                 | Indist.               | Sum of stirling numbers partitions         | 1                                    | stirling number partitions                                                            |
| Indist.               | Indist.               | integer partitions                         | 1                                    | restricted partitions                                                                 |

^1bd745

