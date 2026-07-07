# $$J=E+\lambda C$$
Issue: too much training makes the model learn the pointless small details, need to shred those details and "generalize" the data more, smooth it out. This is mainly because of a lack of data, as more data can smooth out the model automatically, this is for if there's not enough data.

E is your usual loss function

$\lambda$ is the tuning hyper-parameter, which is determined via cross validation

C is the Penalty Constraint, which can be:

# L1: $|w|$ 
Adds $\lambda||w||_1$ This can shrink the solution to 0, so it implements select subset of features automatically
Only a very small fraction of the features actually matter

# L2: $|w|^2$ 
Adds $\lambda||w||^2_2$ to shrink the solution toward 0, but never reaches 0.
weights are evenly distributed across all features, so they all matter

