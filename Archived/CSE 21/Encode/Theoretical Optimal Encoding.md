#Encode
A **Theoretical Optimal Encoding** for length n binary strings with k 1s would use $log_2 \binom{n}{k}$ bits per string, this gets us the number of possible arrangements, or all your options.
- We can store all these arrangements in $log_2 \binom{n}{k}$ bits in a separate pre-composed dictionary.
- Now whenever we get a data and want to decode it, we put the address bit into the dictionary and find the original.
Problem: For something like n=100 k=10, we would have $log_2 \binom{109}{9}$ or 50TB of storage needed for a dictionary
Solution: Use Ranking and Unranking Algorithm to calculate the dictionary entry without storing anything, simulating a dictionary

