$RegL \subset CFG \subset D \subset RE \subset \Sigma^*$

> [!info] Analogy
> - Imagine a Kingdom with a King ($K$) who has Lords ($V$) and Villagers ($w\in\Sigma^*$).
> - Lords ($V$) have subjects ($v\in L(V)$) that he allows into his land. He petitions to the King when he wants to become the King's vassal. He also petitions to the King whenever a Villager wants to join him.
> - In order to decide membership, the King requires a parchment (<>).
> 	- If it's about accepting a Lord, the parchment needs to be the Lord's Laws ($<V>$).
> 	- If it's about accepting a Villager, the parchment needs to be the Lord's Laws along with the Villager ($<V,w>$). The Villager does not belong to the Lord yet.
> - The King can invite the Lord / Villager over if he cannot form a verdict based on parchment alone.
> 	- Can make the petition permanently postpone.
> - The King can either accept, reject, or permanently postpone the Lord's petition.
> - The King is a Recognizer ($RE$) if the King can accept all parchments that fulfills his criteria
> - The King is a Decider ($D$) if the King can accepts all parchments that fulfills his criteria and reject all parchments that does not.
> - A King who can Decide is more competent than a King who can only Recognize. This competency is described more in Mapping Reduction.
> - There are many Kingdoms, each with a different King that has a different rule when deciding what parchments are accepted.
>$$ $$
> - TM $K$ -> King
> - TM $V$ -> Lord / Vassals
> - $<V>$ -> Parchment of Lord's Laws
> - $<V,w>$ -> Parchment of Lord's Laws as well as a Villager
> - $L(K)$- > King's Vassals (Lords)
> - $L(V)$ -> Lord's Subjects (Villagers)
> - $v\in L(V)$ -> One of a Lord's Villagers
> - $w\in \Sigma^*$ -> Random Villager

### Computable
$f:\Sigma^*\rightarrow\Sigma^*$ is TM-computable if $\exists \ TM \ M$
$(q_s,w)\rightarrow...\rightarrow(q_a/q_r,w'), w'=f(w)$
> [!info] Self Explanation
> Function f is computable if there exists a TM s.t. given w on tape, it always halts on f(w) on tape at the end, i.e. it doesn't loop. Basically, it is a function that a TM can replicate.
> 1. starts with w on tape
> 2. always halts / no loops
> 3. outputs f(w) when it halts

### Recognizable
$L(M)$ is the set of strings $w\in\Sigma^*$ such that $M(w)$ accepts
$L=L(M)$ is TM-recognizable
> [!info] Self Explanation
>-  L is recognizable if the TM it represents accepts everything in L. It's not obligated to reject.
> - Confirms membership, but can't confirm non-membership
> - 

$RE=\{L(M)|\text{ M is a TM}\}$
$L(M)=\{w\in\Sigma^*|M(w)\text{ accepts}\}$

### Decidable
$M$ is a decider if $\forall w\in\Sigma^*$, $M(w)$ terminates.
$L=L(M)$ where $M$ is a decider. $L$ is TM-decidable
> [!info] Self Explanation
>-  L is decidable if the TM it represents accepts everything in L and rejects everything not in L and infinite loops.
> - We can get a definite answer on membership or non-membership for any string in $\Sigma^*$
> - Based on HALT, any L that requires information from within TM $M$ that can only be answered via simulation, not just based on the encoding $<M>$, is not decidable.

$L\in D: \text{ if }\exists \ TM \ M$
- $\forall w\in L, M(w)$ accepts
- $\forall w\notin L, M(w)$ rejects 

