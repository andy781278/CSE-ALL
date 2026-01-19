---
aliases:
  - SCC
---
Only in directed graphs, SCCs are components in that graph (a group of vertices) that can all reach each other.

Graphs are always made up of SCCs, no matter how disconnected they are, since a single node can be an SCC.

Decomposition:
a non-DAG can be turned into a DAG if we group all the SCCs together and treat them as vertices.