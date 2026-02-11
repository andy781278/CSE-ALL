You are running a conference, you have a collection of events that each have a start and end time. Schedule the most events that day so that no two events overlap.

### Specification:
Instance: Collection of events $\{(s_1,f_1),(s_2,f_2),...,(s_n,f_n)\}$

Solution format: Subset of events

Constraint: no two events in subset overlap

Objective: function: Solution format -> R

Maximize of Minimize: Maximize

### Pick a method
Think of some greedy methods and go through them to find the best one.
- Shortest duration
- Earliest start time
- Fewest conflicts
- **Earliest end time**

### Implementation
Init Queue S
Sort events by finish time
Put event 1 $E_1$ in S
Set F = $f_1$
For i=2 ... n:
	if $s_i \geq F$:
		enqueue($E_i$,s)
		F=$f_i$
return S

