It's possible that scheduling and synchronization causes all processes to be blocked, and nothing runs


> [!warning] Example
> Thread A and B both needs Lock A and Lock B
> Thread A and B both calls join on each other

More formally:

Deadlock can exist iff the following conditions hold simultaneously:
1. Mutual Exclusion - At least 1 resource must be held in a non-sharable mode like a lock
2. Hold and wait - At least 1 process holding 1 resource and waiting for another resource
3. No preemption - resource can't be preempted, aborted, stopped externally
4. Circular wait - A set of processes such that 1 is waiting for 2, and 2 is waiting for 3

## Waits-for Graph (WFG)
If all resources are single unit and all processes make single requests, then we can represent resource states with a WFG, useful for tracking locks

WFG consists of a set of vertices $P=\{P_1,P_2,..,.P_n\}$ of processes
- A directed edge $P_i \rightarrow P_j$ means $P_i$ has requested a resource (lock) that $P_j$ currently holds, so i waits for j to finish, therefore i depends on j
- Graph cycle means Deadlocks exist

## Prevention
Ensure at least 1 condition cannot occur
1. Mutual Exclusion - make resources sharable (not practical)
2. Hold and wait - processes cannot hold 1 resource when requesting another, process request, release all needed resources at once
3. Preemption - OS may preempt resource (costly)
4. Circular wait - impose ordering (numbering) on resources and request them in order (popular)

## Avoidance
Provide information in advance about what resources will be needed by processes to guarantee that deadlocks will not happen
- Sys only grants resources requests if it knows that the process can obtain all resources it needs in future requests
- avoids circularities
- Touch, hard to determine all resources needed in advance, not practical

## Detection and Recovery
Traverse resource graph looking for cycle, recover by:
- Preempt resource, force a process to release
- Abort process (all process resources freed up)
- Many processes and resources to traverse, expensive to check
- Only invoked based on how likely deadlock is and how many processe are likely to be affected when it occurs