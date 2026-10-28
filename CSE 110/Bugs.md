I lowk already know all this
## Bug Report
How to duplicate the bug
What the behavior is 
What the behavior is supposed to be (doesn't have to be right, just expected)

Compile a list of bugs before fixing any so you can prioritize

## Fixing Bugs
1. Fault Localization - which code is buggy (most of the work)
2. Fault Repair - what do I do about it


> [!NOTE] Advices
> Fix one bug at a time
> slow better
> write test cases for each bug
> commit after each bug fixed

## Strategies to Fault Localization
### Hypothesis Testing
Form a hypothesis:
I suspect that (function/class/module/configuration/logic) is most likely responsible because ()

Testing hypothesis:
To test this hypothesis, I will ()
- Add print statements (I love this)
- Use debugger
- Write a minimal reproduction
- Run a specific test
- Remove suspicious code
- Set something to a known-good constant

Fix and validate:
To fix the issue, I ()
To confirm my fix worked, I ()
If it didn't work, I go back to step 1
Is the fix in the error

Root cause:
The defect originates at (line of code/function/module) because ()
repeat until work

### Backwards Tracing
Go to where the bug originated, and work backwards from where that value came from.

Narrowing the source:
work backwards enough to find root cause

After it works, trace forward again to understand the effects

### Test Case Minimization
Remove all elements of test case that are unnecessary

### Narrow Down the Responsible Code
Replace modules with mock modules that does the right thing

### Divide and Conquer
Either:
A component does not do what it's supposed to do
A component does what it's supposed to do, but thats not what the other component needed

Be explicit about assumptions and expectations

### Regression
The use case previously worked but now is broken
Find the specific change that broke it, Version Control....

### Bad State
After doing X, wrong
Do lots of validity testing via assertions throughout the code to see exactly where it went wrong

