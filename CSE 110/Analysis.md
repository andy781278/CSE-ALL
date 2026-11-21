Analysis can be sound or complete
### Sound
Sound analysis finds all of the bugs
if the sound analysis says its safe, it safe, but sometimes there are redundant bugs
### Complete
Complete analysis won't report false bugs, but might miss some bugs

Most analyses are unsound or incomplete

### Static Analysis
analysis of programs without executing them, find bugs or prove safety properties
Often sound

Liveness: this good thing eventually happens
Safety: this bad thing never happens

Techniques:
- Linters - shallow syntax analysis
- Type checking - ensure program has well-defined semantics
- Data flow analysis - abstract interpretation, is a[i] always within bounds?
### Dynamic Analysis
runs the programs
Often complete

Analysis must be super fast, in general they are either incomplete or unsound.


### Model Checking
consider program to be a state machine, see if any possible states are bad
Draw state transition diagram
make sure transitioning into bad state is impossible

### Abstract interpretation
Analyze program, annotating variables with information about possible values

