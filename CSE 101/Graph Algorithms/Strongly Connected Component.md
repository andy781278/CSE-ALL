---
aliases:
  - SCC
---
Only in directed graphs, SCCs are components in that graph (a group of vertices) that can all reach each other.

Graphs are always made up of SCCs, no matter how disconnected they are, since a single node can be an SCC.

Decomposition:
a non-DAG can be turned into a DAG if we group all the SCCs together and treat them as vertices.

SCC Algorithm(How to make SCC graph):
- Construct $G^R$ (reverse graph)
- Run DFS on $G^R$ and keep track of post numbers, make a list of the ordering from highest to lowest post number
- Run DFS on G and order the vertices in decreasing order of the post numbers from the previous step. Every time DFS increments cc, you have found a new SCC.

Time Complexity:
- Linear time
- Creating $G^R$ is O(|V|+|E|)
- DFS on $G^R$ is O(|V|+|E|)
- DFS on G is O(|V|+|E|)
- Whole algorithm is O(|V|+|E|)