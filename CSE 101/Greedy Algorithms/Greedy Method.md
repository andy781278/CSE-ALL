In some cases, there is sufficient structure that allows you to reach the correct solution by just picking the straightforward best decision at each stage. (Occam's razor?)

It doesn't always work

[[Event Scheduling Problem]]

[[Event Scheduling With Multiple Rooms]]

You need to prove Optimality:
- Prove that it is the best solution compared to any other solution.
- Say GS is greedy solution, and OS is other solution
- Then cost(GS)<=cost(OS) or value(OS)<=value(GS)

How to prove Optimality:

### Modify the solution / Exchange (ExArg)
most general, almost universal

#### Template
- Let g be the first greedy decision.
- Let AS be an arbitrary legal solution that does not pick g.
- There is a solution AS' that does pick g and AS' is at least as good as AS.
1. State what we know: Definition of of g, and that AS meets constraints
2. Define AS' from AS, g(usually by exchanging g with another choice)
3. Prove that AS' meets constraints. Use 1,2
4. Compare value/cost of AS' to AS. Use 2, sometimes 1
Induction:
5. Let g be greedy solution, let I be rest of the problem
6. GS = g + GS(I')
7. AS is any legal solution
8. AS' is defined from AS by the exchange argument
9. AS'=g + some solution on I'
10. Induction: GS(I') is at least as good as any solution on I'
11. GS is at least as good as AS', which is at least as good as AS

#### Example
Correctness proof for earliest end time algorithm for Event Scheduling Problem

- G is the event with the earliest finish time. (First greedy decision: include G)
- let AS be an arbitrary non-overlapping schedule that does not include G (Contradiction)
- Claim: there is a schedule AS' that does include G such that $|AS'| \geq |AS|$
- Let the events in AS be $J_1,...,J_k$, ordered by start and finish times ($J_1 \ne G$)

- Claim: AS' is valid, it does not have overlapping events
- Proof: Since AS is valid, any pair $J_i,J_l$ will not overlap, so it is sufficient to prove that G does not overlap with any of the $J_i$ events, particularly $J_2$.

- Claim: G does not overlap with $J_2$.
- Proof: $f(J_1)\leq s(J_2)$, $f(G)\leq f(J_1)$, $f(G)\leq s(J_2)$

- Induction
- Exchange Argument Claim: GS is better or just as good as AS for any solution AS
- let n = number of events
- Base Case: n=1, then the greedy choice works
- IH (Strong): Suppose n>1 and greedy alg is optimal for any k events for $1\leq k \leq n-1$
- i.e. if |I|<n then for any solution AS(I), $|AS(I)|\leq |GS(I)|$
- Goal: greedy is optimal for any n events
- IS: Let AS be set of events $I=\{ E_1,...,E_n\}$
- Then, by exchange argument, there is a valid solution AS' that contains the first greedy choice and $|AS|\leq |AS'|$
- AS' = G U S(I') where I' is the set of all events that don't conflict with G
- |I'|<n so by IH, $|S(I')|\leq|GS(I')|$
- Conclusion:
- $|AS|\leq |AS'| = |\{G\} \cup S(I')|\leq |\{G\} \cup GS(I')| = |GS(I)|$
- GS is greater or equal to any AS, therefore it is optimal


Proving Kruskals() in Exachange
- Take the alternative description of Kruskals
	- Normal, but when you add the lightest edge, you turn those two vertices into a single one.
	- Repeat until no more edges
- Proof:
- Let G=(V,E) be undirected connected graph with positive edge weights
- Let g be the first greedy choice (lightest edge)
- Let OS be spanning tree that does not include g
- Create OS':
	- must include g
	- must be spanning tree
	- must be lighter or equal to OS
- Make OS' by adding g to OS (creating a cycle), and deleting the heaviest edge h in that cycle
- Then OS' is still a spanning tree, and Total weight of OS' is less or equal to OS
	- because we exchanged g for h, and w(g)<=w(h)

- Induction
- Base case n=1
- IH: for some n, Kruskals is optimal for n-1 vertices
- G with n vertices
- OS be some arb sol of G
- Then by exchange, there exist a sol OS' that includes g and lighter or equal to OS.
- OS'={g}US(G') where G' is the meta-graph obtained by fusing the endpoints of g together
- By IH, |Krus(G')|<=|S(G')| because G' has n-1 vertices
- TW(OS) >= TW(OS')={g}UTW(S(G'))>=w(g)+TW(GS(G'))=TW(GS(G)))

### Greedy-stays-ahead
more intuitive
- Start with an arbitrary solution OS and compare all of the greedy solution GS to all of OS instead of just the first greedy move.
- Induct on the greedy choices rather than on the size of the input.

#### Example
let's do events problem again

- Consider input I with n events $E_1,E_2,...,E_n$
- Let OS(I) be some arbitrary set of non-conflicting events, OS(I)=$[J_1,J_2,...,J_k]$
- let GS(I) be the outcome of the greedy strategy
- GS(I) = $[G_1,G_2,...,G_l]$
- show $k\leq l$

- Claim: $Finish(G_i) \leq Finish(J_i)$ for all i
- Proof: induction on i
- Base Case: $Finish(G_1) \leq Finish(J_1)$ by greedy choice
- IH: for some i>=1, assume that $Finish(G_i) \leq Finish(J_i)$
- we want $Finish(G_{i+1}) \leq Finish(J_{i+1})$
- IS: Among all events that start after $G_i$ ends, $G_{i+1}$ ends earliest
- $f(G_i)\leq f(J_i) \leq s(J_{i+1})$
- since $J_{i+1}$ starts after $G_i$ ends, $f(G_{i+1})\leq s(J_{i+1})$

- Prove $k\leq l$ (contradiction)
- Suppose k>l where |OS|=k, |GS|=l, or OS>GS
- Then $G_l$ is the last greedy choice so that are no events that start after $G_l$ finishes
- Then $Finish(G_l)\leq Finish(J_l)$
- And $Finish(J_l)\leq Start(J_{l+1})$
- This implies event $J_{l+1}$ that starts after the last greedy choice
- This is impossible
### Achieves-the-bound
also comes up in approx LP, network flow
- Define some progress measure
- Order the decisions in OS to line up with GS
- Prove by induction that the progress after the ith decision in GS is at least as big as in OS
- Assume by contradiction that OS is strictly better than GS
- Use progress argument to arrive at the contradiction

#### Example
- For Event scheduling with multiple rooms, it reveals a bound when you find the peak cost of the solution
- show this bound is also a lower bound on the cost of any other solution
- showing $Cost(GS) \leq Bound \leq Cost(OS)$
- Allows the two inequalities to be separated
- Implies Cost = Bound

- Let k be the number of rooms for the GS
- Claim: at some point t, |B(t)| = k
- Proof:
- Let t be the starting time of first event scheduled in room k
- Then room k is the minimum room number available at the time, or else the event will go to an available room in a different room
- There were events going on in all other rooms
- Therefore |B(t)| = k at some point t

- Let GS be greedy solution, k = Cost(GS), the number of rooms used in the greedy solution
- Let OS be any schedule, R=Cost(OS) the number of rooms used in OS
- By Bounding lemma, $R\geq L = max(B(t))$
- By achieves-the-bound lemma, $k=|B(t)|\leq L$ for some t
- Putting the two together, $Cost(GS) = k \leq L \leq R = Cost(OS)$
- Thus the greedy solution is optimal