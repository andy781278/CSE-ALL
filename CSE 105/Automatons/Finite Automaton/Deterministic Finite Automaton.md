---
aliases:
  - DFA
---
Definition: A DFA is a 5-tuple $M = (Q,\Sigma,\delta,s,F)$ where:
- $Q$ is a finite set of states (vertices)
- $\Sigma$ is an alphabet (input)
- $\delta: Q \times \Sigma \rightarrow Q$, where $\delta(q,a) \in Q$, and it maps where the edges come from and go to (edges)
- $s$ is the start state
- $F \subseteq Q$ is called accepting states, where output is accept

> [!NOTE]
> Define computation mathematically
> Similar to Finite State Machine
> A graph where the vertices represent states, and the edges represent input. you traverse through the graph from the given sequence of inputs, and then determine states where output is 1

### computation
The **computation** of DFA $M = (Q,\Sigma,\delta,s,F)$ on input $w \in \Sigma^*$ is the sequence $q_0, w_1, q_1, w_2, q_2, w_3, ..., w_n, q_n$ of $q_i \in Q$ and $w_i \in \Sigma$ such that
- $w=w_1 w_2 ... w_n$
- $q_0 = s$
- $q_{i+1}=\delta(q_i,w_{i+1})$
the automaton outputs the state for every input, the output can be accepting or rejecting:
- accepting if $q_n \in F$ or state is accepting state
- rejecting if $q_n \notin F$ or state is not accepting state

$\delta^*: Q \times \Sigma^* \rightarrow Q$
$\delta^*(q,\epsilon)=q$
$\delta^*(q,aw)=\delta^*(\delta(q,a)=q,w)$

$L(M) = \{w\in\Sigma^* | \delta^*(s,w)\in F\}$

### regular
If a language can be defined by a DFA, then it is **regular**:
$L\subset \Sigma^*$ is regular if $\exists M$ (DFA)  such that $L(M)=L$

#### reg. lang. is closed
The class of regular languages is closed under $op(L_1,L_2,...,L_k)=L$
if $\forall L_1,...,L_k$ are regular, then $op(L_1,...,L_k)$ is regular

##### Are Regular Languages closed under any operation op?
> [!abstract] Are Regular Languages closed under set difference ($\backslash$) ?
> Let $op(L_1)=\Sigma^* \backslash L_1$
> Assume L is a regular language
> By def. $\exists M$(DFA) such that $L(M)=L$
> Let $M = (Q,\Sigma,\delta,s,F)$
> WTS(want to show): $\exists M'$ such that $\Sigma^* \backslash L = L^c = \bar L$
> Let $M'= (Q,\Sigma,\delta,s,\Sigma^* \backslash F)$
> $L(M')=\bar L$
> Q.E.D.

> [!abstract] What about Union?
> Let $M_A,M_B$ be DFA for A and B
![[CSE105 Proof Reg. Lang. closed under union.excalidraw]]
> You make a new state that automatically goes to both $M_A$ and $M_B$ with $\epsilon$, which is automatic
> Then, we keep both DFA's accepting states, accepting the whole thing if we accept either one.


> [!abstract] Concatenation ($A \cdot B$)
> we do a similar thing, and we connect the accepting states of $M_A$ to the starting state of $M_B$
> This way, the input has to pass both $M_A$ and $M_B$ to pass the whole thing

> [!abstract] If $A$ is regular, then $A^*$ is regular
> We have to make sure every loop is accepting, including the lack of a loop
> Make arbitrary new state, make it accepting, connect it with $\epsilon$ to the starting states s. 
> Connect accepting states to the starting states.


> [!abstract] Every Regular Expression can be an NFA
> $\forall RegEx \ R \quad \exists \ NFA \ \  N \ \  s.t. \ L(N)=L(R)$
> Proof: By cases (induction on the structure of R):
> 1. $R=\emptyset$: a single state with no accepting states and nowhere else to go
> 2. $R=\epsilon$: a single accepting state
> 3. $R=a$: a starting state that takes input a to go to an accepting state
> 4. $R=R_1 \cup R_2: N_1, N_2 \rightarrow N_1 \cup N_2$
> 5. $R=R_1 \cdot R_2: N_1 \cdot N_2$
> 6. $R = R_1^*: N_1^*$

### Flaws
DFAs have no memory, so they can't describe languages that requires memory
$L_{nn}=\{0^n1^n | n \geq 0\}\subset L(0^*1^*)$
 $\forall \text{ DFA } M, L(M)\neq L_{nn}$
This is also a flaw for NFA and GNFA. None of them have memory.

### File Format
If we want to store a DFA into a string, how do we do it?
Given DFA($\Sigma=\{0,1\}$), we need to make a string that can store it, we can only use 4 words alphabet
$|q|=k+1,k=log_2(n)$
string: $q_0 q_1 ... q_{n-1} [[]e[]]...$
- since same length, we don't need a delimiter and just read k symbols in at once for each state
- the extra symbol describes if its accepting state or not
- next is the transitions, which is described by $[[a]e[b]]$, where e on state a goes to state b. The start state is []
Regular Expression: $([[(0\cup 1)^*] (\epsilon \cup 0 \cup 1)[(0 \cup 1)^*]])^*$
- states without transition: point epsilon transition to itself