NFA with a stack
#####  $$(Q,\Sigma,\Gamma,\delta,s,F)$$
$s \in Q, F \subseteq Q$
$\delta:Q\times\Sigma\times \Gamma \rightarrow p(Q\times\Gamma)$

Transitions: $a,b \rightarrow c$
- reading a input, pop b from stack, push c onto stack
- $a\rightarrow c$ means pop a and push c
- $\rightarrow c$ means push c

push $\$$ onto the stack as a marker to tell if you've hit the bottom of the stack

pop by going down a consume loop if there's a symbol on top of the stack, it should eliminate the input we want as long as it's done right. This way we can reach the variable and use an expand loop to expand the variable.

> [!info] Self Explanation
> $\times$ means you need more input, unique input for each variable.
> so $Q\times\Sigma\times \Gamma \rightarrow p(Q\times\Gamma)$ means take in a state, a symbol, and a stack symbol, and outputs a state, and a stack symbol
> The input stack symbol is what you're popping off the stack
> The output stack symbol is what you push onto the stack
> This configuration is fully customizable so you can accomplish memory via the stack.
> Any of those variables except for $Q$ includes $\epsilon$

### Convert from Context Free Grammars
- First, make 4 states: starting state connected to s state with $\epsilon,\epsilon\rightarrow\$$, then s state to loop state with $\epsilon,\epsilon\rightarrow S$, then loop state connected to accepting state with $\epsilon,\$\rightarrow\epsilon$.
- Then, take the rules, for each option for each rule, make a loop on the loop state with as much intermediate states as the rule option length, each state representing one of those elements. Let's call this an expand loop.
- Additionally, $\forall a \in \Sigma$, make $|a|$ loops, and put $a,a\rightarrow\epsilon$ transition on each loop, let's call it a consume loop.

### 2-PDA
To represent something with more than 2 variables like
$L=\{a^nb^na^n \ | \ n \geq 0\}$
We need to modify our PDA, since the old one doesn't really remember more than the stack, which is limited to two variables

$2-PDA: (Q,\Sigma,\Gamma,s,F,\delta)$
$\delta:Q\times\Sigma\times\Gamma^2_\epsilon\rightarrow Q\times(\{0,1\}\times\Gamma_\epsilon)^2$

We use a more formal operational style for describing the machine by using a sequence of configurations

##### Configurations
A config is a complete snapshot of the machine, for this 2-PDA, the Config falls in the domain: $Conf=Q\times\Sigma^*\times\Gamma^*\times\Gamma^*$

Input $w\in\Sigma^*$
Init(w)=$(s,w,\epsilon,\epsilon) \in Conf$
Step: $Conf \rightarrow Conf \cup \{0,1\}$

$Step(q,\epsilon,\gamma_1,\gamma_2)=\begin{cases} 1 & \text{if } q\in F \\ 0 & \text{otherwise} \end{cases}$

$Step(q,aw,\gamma_1,\gamma_2)=(q',w,\alpha_1 \cdot pop(b_1,\gamma_1),\alpha_2 \cdot pop(b_2,\gamma_2))$
$(q',(b_1,\alpha_1),(b_2,\alpha_2))=\delta(q,a,fst(\gamma_1),fst(\gamma_2))$
$b_1,b_2\in \{0,1\}, \alpha_1,\alpha_2 \in \Gamma_\epsilon$
$fst(\alpha\gamma)=\alpha$
$fst(\epsilon)=\epsilon$
$pop(b,\alpha\gamma)= \begin{cases} \gamma & \text{if } b=1 \\ \alpha\gamma & b=0 \end{cases}$
$pop(b,\epsilon)=\epsilon$

