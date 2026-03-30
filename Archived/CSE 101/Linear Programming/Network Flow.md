Instance: Directed Graph with non-negative edge weights, called the capacity of edges. Two vertices s: source and t: sink

Solution format: assignment of non-negative values to each edge

Constraints: any vertex except for s, t total flowing in = total flowing out. Flow along edge cannot exceed capacity of edge

Objective: Max total flow out of s=total flow into t

Basically: pass the most amount of flow possible from start to finish vertex



question: is there any flow in residual edges?

Use the [[Ford Fulkerson Method]], we can represent prob of improving flow as anotehr flow problem for the residual graph

if f(e) is flow on edge e and c(e) is capacity of edge e then change the capacity to c(e)-f(e) and add f(e) to capacity of reverse edge

if f is the flow in the og graph, and f' is residual graph flow, then we can add that shit tgt and its fine

by reversing the edge, we kind of lose that path, and go on another, we keep going until no path is left

Then we add them all together

how? We cut the graph, find the minimum cut. The maximal flow must be from that minimum cut.

It can take forever, and it keeps on improve forever