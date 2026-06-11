##### Find
Time (balanced): $O(log(n))$
Time (unbalanced): $O(n)$
Time (worst case): $O(n)$
##### Insert
Time (balanced): $O(log(n))$
Time (unbalanced): $O(n)$
Time (worst case): $O(n)$
##### Remove
Time (balanced): $O(log(n))$
Time (unbalanced): $O(n)$
Time (worst case): $O(n)$
- Case 1: node u has no children
	- delete u
- Case 2: node u has 1 child
	- have u's parent point to u's child
- Case 3: node u has 2 children
	- replace u with u's successor

##### Successor
Case 1: node u has right child
- traverse down right and then go as left as possible
Case 2: node u has no right child
- traverse up until your node is a left child of another node, then that parent is it