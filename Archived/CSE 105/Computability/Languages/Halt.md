
> [!info] Analogy
> King $Halt$ takes $<V,v>$ parchments where Lord V reaches a verdict with Villager v without deliberating forever

$L_{HALT}=\{<M,w>|\text{M is a TM and halts on w}\}$

$L_{HALT}$ is not decidable, it is recognizable
$L_{HALT}\in RE, L_{HALT}\notin D$

This is because to know if it is decidable, we need to simulate M, which can loop forever. In other words, we can't know for sure what M accepts/rejects unless we simulate it.