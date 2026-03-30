Possion Distribution

# Discrete
Suppose some event is known to occur on an average 𝜆 times in every fixed unit of time. Then a Poisson random variable, 𝑋∼Poi(𝜆), expresses the probability of a given number events actually observed in this fixed unit of time.
$$supp(𝑋)=1,2,3,…$$
$$P(X=k)=\frac{\lambda^k*e^{-\lambda}}{k!}$$
$$E(X)=\lambda$$
$$Var(X)=\lambda$$

if $X \textasciitilde Poi(\lambda), Y \textasciitilde Poi(\gamma)$ and $X \perp Y$, then
$$X+Y \textasciitilde Poi(\lambda + \gamma)$$