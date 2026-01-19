#Encode 

**Simple Directed Graphs** are graphs with no self loops and no parallel edges.
![[Untitled.png]]

There are $2^{n(n-1)}$ different simple directed graphs with n vertices.
That means we can safely identify each graph uniquely with n(n-1) bits

![[Pasted image 20251124154557.png]]

There are $2^{\binom{n}{2}}$ different simple undirected graphs with n vertices.
That means we can safely identify each graph uniquely with $\binom{n}{2}$ bits

Undirected graphs are symmetric, so we only need 1 triangle to get all the data

![[Pasted image 20251124155141.png]]

![[Pasted image 20251124155119.png]]

![[Pasted image 20251124155103.png]]