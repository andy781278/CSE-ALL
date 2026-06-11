---
aliases:
  - GNFA
---
$\delta:(Q\backslash \{f\})\times(Q \times \{s\}) \rightarrow RegEx$
- Edges are all RegEx instead of coming from $\Sigma$
- no incoming edges from starting state
- only 1 accepting state
	- No outgoing edges from accepting state

### Converting DFA to GNFA
Our goal is to collapse everything in DFA down to 2 states, starting and accepting states, and their transition becomes the RegEx we are looking for.
- Every starting state is connected to a new starting state with $\epsilon$ transition.
- Every accepting state connects to a new accepting state with $\epsilon$ transition.
- Every edge is an element in the RegEx
- Every loop is that input star-ed
- Loops created by transitioning to multiple states instead are replaced by a self loop that has the RegEx equivalent of the multi-state loop
- Make sure to do this for both directions, they can't merge
- $\cup$ the new Regex with the old one if there's already an edge there.
- Usually easier if you remove the least connected state at that time 