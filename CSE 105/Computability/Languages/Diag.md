
> [!info] Analogy
> King $Diag$ takes $<V>$ parchments where Lord V would reject his own parchment $<V>$ if it were handed to him as a villager

$Diag=\{<M>|\text{ M is a TM, }<M>\notin L(M)\}$

> [!info] Diag
> Diag is a language that accepts the encoding of a TM M, but only encodings that is not in the language of that M.
> 

Claim: $Diag$ is not recognizable, or $Diag \notin RE$
Proof: Assume $Diag \in RE$
By Def, $Diag=L(M)$ for some M(TM)
$w=<M>\in Diag \leftrightarrow <M> \notin Diag$

> [!info] $Diag \notin RE$
> Diag is not recognizable, as in there's no way to guarantee given a set of inputs they will be accepted correctly.
> It also means there's no TM that can represent the language.

