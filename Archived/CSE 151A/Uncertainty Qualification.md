Sometimes it's better to say you're not sure rather than to give a solid yes/no answer

Sometimes you give percentages as an answer instead of yes/no

Accuracy: how right you are in picking the answer
Probability fidelity: does your probability output actually match the frequency of that answer being chosen

### Aleatory
Intrinsic uncertainty
Randomness baked into the data generating process
- overlapping classes, hidden covariates
- may stay noisy despite infinite data
- Doesn't shrink with more data

### Epistemic
Basically, not enough data, based on a finite training set
Uncertainty we might shrink
- finite n shift misspec/bad optimization
- more data and richer models shrink this
- Shrinks with more data
#### Bootstrap
- split data D into B smaller samples
- get estimators per smaller sample B*
#### Cross-validation
We can split data into k folds, and for each iteration from 1 to k, we skip that particular fold and train the rest, then we find the fold with the best performance
#### Ensembles
average or compare several trained models

## Calibration
Scores $s(x)\in[0,1]$ aim at $P(Y=1|x)$

Calibration: if $s(X)\approx p, E[u]\approx p$
$E[Y|s(x)\approx p]\approx p$
Check: histogram $s$ vs. $\bar y$

#### Binning Sketch
Bins=s ranges; stacks = labels 0/1
![[Pasted image 20260609201548.png]]
Bucket means $\hat s$ vs. positive rate

![[Pasted image 20260609201651.png]]
It is calibrated if it is on the diagonal

![[Pasted image 20260609201717.png]]
Forecasts >> reality means miscalibrated

### Isotonic Regression
For when model scores s(x) is miscalibrated
Post-hoc fix: learn a map $\hat r: [0,1]\rightarrow[0,1]$ on a held-out calibration seet
$C=\{s^{(i)},y^{(i)}\}^{n_{cal}}_{i=1}$ (C disjoint from train and test)
At deployment: output $\hat r(s(x))$ instead of raw s(x)
Isotonic constraint: $\hat r$ is non-decreasing
$s_1<s_2 \rightarrow \hat r(s_1)\leq \hat r(s_2)$
Higher model confidence -> higher calibrated probability (never flip the ranking)

![[Pasted image 20260609204401.png]]
![[Pasted image 20260609204833.png]]
![[Pasted image 20260609210634.png]]

### Proper Scoring Rules
![[Pasted image 20260609210759.png]]
Both A and B are correct, but A is closer to 1/0, and if A makes a mistake, they'll be more wrong than B, since they're further away from 0.5. So B is actually more accurate here even though they picked safer options.

![[Pasted image 20260609211122.png]]
You can't just be right, you have to also know when you can assign high/low probabilities when evidence says so, that's sharpness

![[Pasted image 20260609211242.png]]
![[Pasted image 20260609211413.png]]
Both Brier and Log loss are proper scoring rules, meaning the only way to minimize them in expectation is to predict the true probabilities. So they actively reward good calibration, not just good rankings.

