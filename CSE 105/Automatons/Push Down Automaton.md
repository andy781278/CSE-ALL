NFA with a stack
#####  $$(Q,\Sigma,\Gamma,\delta,s,F)$$
$s \in Q, F \subseteq Q$
$\delta:Q\times(\Sigma \cup \{\epsilon\})\times (\Gamma\times \{\epsilon\}) \rightarrow p(Q\times(\Gamma^{*(\leq2)} \cup \{\epsilon\}))$

Transitions: $a,b \rightarrow c$
- reading a input, pop b from stack, push c onto stack
- $a\rightarrow c$ means pop a and push c
- $\rightarrow c$ means push c

push $\$$ onto the stack as a marker to tell if you've hit the bottom of the stack

pop by going down a consume loop if there's a symbol on top of the stack, it should eliminate the input we want as long as it's done right. This way we can reach the variable and use an expand loop to expand the variable.

### Convert from Context Free Grammars
- First, make 4 states: starting state connected to s state with $\epsilon,\epsilon\rightarrow\$$, then s state to loop state with $\epsilon,\epsilon\rightarrow S$, then loop state connected to accepting state with $\epsilon,\$\rightarrow\epsilon$.
- Then, take the rules, for each option for each rule, make a loop on the loop state with as much intermediate states as the rule option length, each state representing one of those elements. Let's call this an expand loop.
- Additionally, $\forall a \in \Sigma$, make $|a|$ loops, and put $a,a\rightarrow\epsilon$ transition on each loop, let's call it a consume loop.