#Probability
$$P(E)=P(E|F)P(F)+P(F|E)P(E)$$
$$P(E)=P(E|F)P(F)+P(E|\bar{F})P(\bar{F})$$

Additionally:
Let $\{B_1,B_2,...,B_k\}$ be the partition of sample space S such that any two $B_k$ are mutually exclusive and all B add to S


Problem:
A: patient tested positive
B: patient is infected

P(A|B) = 0.95
P(A|$\overline B$) = 0.08
P(B) = 0.01

What is P(B|A)?
P(B|A) = $\frac{P(A|B)P(B)}{P(A)}$
P(B|A) = $\frac{P(A|B)P(B)}{P(A|B)P(B)+P(A|\overline B)P(\overline B)}$
P(B|A) = $\frac{0.95P(B)}{0.95P(B)+0.08P(\overline B)}$
P(B|A) = $\frac{0.95*0.01}{0.95*0.01+0.08*0.99}$

