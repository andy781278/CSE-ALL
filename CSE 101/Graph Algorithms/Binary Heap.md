A complete binary tree of vertices with the property that each key value of an object is less than or equal to the key value of its children.

Used in PQs

The children of $a_i$ are $a_{2i}$ and $a_{2i+1}$. The parent of $a_i$ is $a_{i-1}$

### deletemin
deleting a parent messes things up. We take the very last key and replace the missing vertex with it. Since we took away the last key, no nodes depend on it.

Now we compare this new node with its children, and swap if the child is smaller. Do this until everything is fine again.

This takes $O(log(n))$ instead of $O(n)$

Complication: finding a vertex in the binary heap takes O(n), which is too much man. Keep an address book, like a hashmap, so it's O(1) for searching instead.