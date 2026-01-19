 #Graph
Graphs are mathematical objects/virtual data structures comprised of vertices and edges.

Graphs can be Directed or Undirected
Undirected - Degree Sum = 2 * edges
Directed - Indegree sum = Outdegree sum = edges

Walk: A route that alternates vertexes and edges
Trail: A walk that doesn't repeat edges
Path: A walk that doesn't repeat edges and vertices, Simple Path
Trivial Path: every vertex has a trivial path to itself with length 0
Closed Walk: A walk that starts and ends on the same vertex
Circuit: A trail that starts and ends on the same vertex, length > 0, closed trail
Cycle: Simple Path that starts and ends on the same vertex, length > 0, Closed path
Loop: An edge that points a vertex to itself

Complete Graph: A graph that connects every vertex to every edge, Undirected, $K_n$
Bipartite Graph: A graph with two sets of vertices $V_1, V_2$, and no vertices in the same set connects to each other

Tree (Undirected): an undirected, connected graph with no cycles
Tree (Directed): Rooted Tree, A directed graph with the property that each vertex has exactly 1 edge pointing to it, except for the root, which has zero.

Connected (Undirected): every point can go to every other point
Weakly Connected (Directed): if made into undirected, every pt can go to every other point
Strongly Connected (Directed): every pt can go to every other pt

Eulerian Trail is a trail where each edge occurs exactly once (Easy to find)
- Eulerian Circuit is a Eulerian Trail that starts and ends on the same vertex
- degree of intermediate vertexes must be even
- has either 0 or 2 odd-degree vertices
- connected
- Finding Eulerian Trail
	1. Find the 2 odd-degree vertices
	2. Start from one of them, and loop:
		1. go down an edge that's not a bridge (when removed, graph becomes disconnected)
		2. After going, remove the edge that was just went, and update the degrees accordingly, there should now still be either 0 or 2 odd degree edges
		3. Choose a new edge from the new vertex, be sure to also not choose a bridge
		4. Visit every node on that side of the bridge before crossing the bridge\
		5. Do the same on the other side

Hamiltonian Path is a path where each vertex occurs exactly once (Hard to find)

Directed Acyclic Graph (DAG)
- A directed graph with no cycles
- When there is cycles, there is no good ordering for the vertices
- Topological Ordering or Linearization of a graph is a sorted list of all its vertices such that for each edge $(v,w)$ in the graph, v comes before w in the list
- vertices with no incoming edges: Sources
- vertices with no outgoing edges: Sinks
- Make a Topological Order:
	1. While there are still sources:
		1. run through the sources, output them, then remove them and their outgoing edges, update this to make new sources

Unrooted Trees
- Undirected Graph with no cycles, connected
- simple path between any two vertices (but just 1)
- Leaves in a tree are vertices of degree 1 (or 0 for a tree with a single vertex)
- All trees with n vertices has n-1 edges
- A set of trees is called a forest

A tree with two or more vertices will always have a vertex of degree 1 (leaf)
Proof by contradiction:
- Assume in a tree, every vertex has degree > 1
- pick any vertex and go to its neighbor, since the neighbor has 2 degrees or greater, then it can go to another vertex that's not the original vertex
- This can go on forever, which is not possible unless it cycles, but trees cannot cycle
- contradiction

A tree with n vertices has n-1 edges
Proof by Induction:
- Base Case: if a tree only has 1 vertex it has 0 edges
- Ind Hyp: Let n>=1, suppose all trees with n vertexes has n-1 edges
- Ind Step: (show n+1 v has n e)
	- Let G be a tree with n+1 v, by previous lemma, g has at least 1 leaf v, if you remove that leaf v, then the tree becomes ind hyp tree, add the vertex and edge back, now you have n+1 v and n e

Rooted Trees:
- a dag that has a defined vertex as a root with no incoming vertexes, every other v has exactly 1  incoming e
- Height of a v is given by recurrence h(v)=h(p(v))+1 if v is not root, h(r)=0

Binary Tree:
- rooted tree where every vertex has at most 2 children
- Max height with n vert - n-1
- min height with n vert - $log_2(n+1)-1$

Binary Search Tree:
- Root node has value r
- every node to the left has smaller value than r
- every node to the right has greater value than r
- This recurrence is at every node

![[Encoding Graph]]