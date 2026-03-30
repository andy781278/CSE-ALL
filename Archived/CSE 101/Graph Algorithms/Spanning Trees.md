---
aliases:
  - Spanning Tree
---
A spanning tree of an undirected graph G=(V,E) is a subgraph G'(V,E') such that
- G' is a tree and
- all vertices in V are connected
- An output tree of DFS or BFS is a spanning tree

Minimum spanning Trees are spanning trees that have the lowest combined edge weights

Proof: The minimized graph is always a tree
- Assume there are connected minimum spanning graphs that's not a tree
- Then there is a cycle
- cut away cycle edges and the graph stays connected
- but it reduced the cost compared to the original
- so the original wasn't a minimum, but it assumes minimum
- contradiction

Two ways to find minimum Spanning Trees

### Prims
Pick the next lightest edge that keeps the graph connected and does not create a cycle
![[Prims()]]

### Kruskals
Pick the next lightest edge that doesn't create a cycle
![[Kruskals()]]

### Proving

#### Cut property
Suppose G'=(V,T) is a MST of G=(V,E), X subsets T.
S subsets V such that there is no route from S to not S (V-S) using edges from X
Let $e \in E$ be the lightest edge connecting S to V-S
Then X U {e} must be a part of MST

Proof:
Case 1: $e \in T$
- Then X U {e} $\in T$ and we assume that T is the set of edges of an MST so X U {e} must be a part of that MST
Case 2: $e\notin T$
- Consider T U {e}. Since T is the edge set of a connected tree, T U {e} creates a cycle. Cycle contains e.
- There must be $e' \in T$ that connects S to V-S.
- The edge set TU{e} - {e'} is still a tree
- w(e) $\leq$ w(e')
- cost(T U {e} - {e'}) = cost(T) + w(e) - w(e')
- cost(T U {e} - {e'}) $\leq$ cost(T)
- But cost(T) is supposed to be minimal, so only case where it works is if they're equal
- cost(T U {e} - {e'}) = cost(T)
- X U {e} subsets T U {e} - {e'}

#### Apply Cut Property to Prims and Kruskals
Claim: After each iteration, the set of edges X (explored) is the subset of MST

##### Prims
Prims separate the graph (V) into vertices that is in the MST already (S), and ones that are not (V-S). Then we pick the lightest edge e that goes from connected to the not connected (S to V-S).

##### Kruskals
Kruskals selects edges from the lightest to the heaviest, as long as it doesn't form a cycle. The next lightest edge e connects two parts together. (Doesn't matter how you group the two parts, as long as e connects them together)

