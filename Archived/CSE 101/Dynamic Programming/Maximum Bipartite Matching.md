Cookie monster problem, select from 2d int map, can't use same col or row again, find max sum

Make it into a graph with one axis mapped to the other, choose random valid answer, then map those as positive edges with the others as negative and the opposite direction. Use bellman ford algorithm and when there's negative cycle, improve it by reversing that cycle, repeat until no more negative cycles, and that's when we've reached optimal solution

Bellman-Ford is O(|V||E|)=$O(n^3)$. Each negative cycle will def increase sum by 1, so in worst case, you'll have to increase C times where C is the total weights of all numbers

Total Runtime

$O(Cn^3)$ (very pessimistic)

There is an issue with local optima
- if you find a local optima, you can't find global max
- common pitfall

This is when we use Linear Programming
