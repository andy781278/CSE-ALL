---
aliases:
  - TST
---
##### Find
Time: $O(L)$
Time (worst case balanced): $O(L log(n))$
Time (worst case unbalanced): $O(Ln)$
##### Insert
Time: $O(L)$
Time (worst case balanced): $O(L log(n))$
Time (worst case unbalanced): $O(Ln)$
##### Remove
Time: $O(L)$
Time (worst case balanced): $O(L log(n))$
Time (worst case unbalanced): $O(Ln)$

chars are stored in nodes, end node is marked

When traversing, if this char is not it, go left for smaller and right for bigger, skip that one, otherwise count that one

Ternary Search Trees are a bit slower than Multiway Tries, but they are significantly more space-efficient, and as a result, they are often chosen as the data structure of choice when people implement lexicons.

Ternary Search Trees is a nice middle-ground between the time-efficiency of a Multiway Trie and the space-efficiency of a Binary Search Tree.