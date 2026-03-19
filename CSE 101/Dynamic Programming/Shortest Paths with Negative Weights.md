
Given a graph with vertices v0,...,vn-1, and maybe negative edge weights, find len of shortest walk from v0 to all other using at most T edges

1. subproblems

Let B[i,t] be the shortest path from v0 to vi using at most t edges

2. base cases

B[0,t] = 0

B[i,0] = $\infty \text{ for i} > 1$

3. recursion

what is the second to last vertex in that shortest path?
we need the minimum of all of the last vertex's incoming neighbors

case 0: v0 is second to last
case 1: v1 is second to last 
...
case n-1: vn-1 is second to last

We let every vertex to have the potential to be second to last vertex.
Then we take the min of all of them as if they were the 2nd to last

B(i,t) = min{B(0,t-1)+w(v0,vi), B(1,t-1)+w(v1,vi),...,B(n-1,t-1,+w(vn-1,vi))}

= min(B(j,t-1)+w(vj,vi)) for all vertices j

weight is infinite if there is no edge possible

4. ordering

We need to compute column by column, if the column is the vertices ,and rows are the t requirements. This is because every element requires all of the previous row's info to find its min


What should t be? (maximum budget) it should be n-1 as that is the maximum amount of edges in a walk to reach every vertex

So order the t parameter from 0,1,...,n-1 where n is the number of vertices

[[Bellman Ford Algorithm]]

