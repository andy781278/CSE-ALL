Def: edges in undirected graphs that has been explored but not in the dfs tree of that graph.
- If there's a back edge, there's a cycle in the graph
- Check if the edge is a back edge by checking (u,v), prev(u)=v or prev(v)=u, if neither, then has to be back edge.
- Removing the back edge does not disconnect the graph, moving a non back edge will disconnect a graph.

back edge in a directed graph is an edge that leads a vertex to its ancestor