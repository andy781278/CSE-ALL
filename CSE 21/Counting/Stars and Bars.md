#Counting
Identical vs Distinct objects:
5 different knights into 3 castles, all of them has to go to a castle, more than 1 knight can be in 1 castle
$3^5$ arrangements, each knight has 3 choices, 5 knights in total.
Now, they are identical robot indistinguishable knights, what changes?
now the way to do it is to pretend they are on a line, fences separate castles that act as 1, and knights are 0, now we have a binary string with [[Fixed Density]]. 0010100 for example, so we're simply picking what positions for the 1 to go, so $\binom{7}{2}$. This only works if the castles are distinguishable.

If i have n knights and k castles, then I need:
n stars
k-1 castles
or n zeros and k-1 ones
$$\binom{n+k-1}{k-1}$$
