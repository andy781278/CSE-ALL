##### Insert
Time: $O(log(n))$
- Put in element to last inorder
- Bubble up, if parent doesn't match, swap
##### Peek
Time: $O(1)$
##### Pop
Time: $O(log(n))$
- replace root with last inorder
- trickle down and replace with one child until you're fine