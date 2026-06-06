##### Find
Time: $O(log(n))$
##### Insert
Time: $O(log(n))$
1. For every node you come across with 2 red children, turn them both into black, and turn yourself red
2. all roots are black
3. perform AVL rotation on any 2 red in a row, then swap color between root and child so that root is black and children is red (don't do step 1 yet, do it next time)
##### Remove
Time: $O(log(n))$

Better for many Insert/Remove calls

Rule:
Every node (not including itself) has to hit the same number of black nodes on every path it has down to NULL, which is inexistent children