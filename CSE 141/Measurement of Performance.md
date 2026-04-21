 $$Performance = 1/Execution Time$$
$$Speedup_{A/B} = Performance_A / Performance_B$$
$$Speedup_{A/B} = Execution Time_B / Execution Time_A$$
$$PercentageIncrease=(Speedup-1)\times100$$

$$Effective Cores = CPUTotalTime/Real Time$$
$$CPU Total Time=User Time + System Time$$

$$CPUTime= \frac{TotalClockCycles}{DynamicInstructionCount}\times Instruction Count \times ClockCycleTime$$
$$CPU ExecutionTime=CPU ClockCycles\times ClockTime$$
$$CPUClockCycles=CPI \times Instruction Count$$
$$CPI=Average CyclesPerInstruction=\frac{TotalClockCycles}{DynamicInstructionCount}$$


- Execution time
- Throughput (operations / time) (speed)
	- Not very good, since different operations take different time to perform, one can get a high throughput with an easy set of operations and falsely claiming it's fast.
- Frame rate
- Responsiveness
- Performance / Cost / Power / Energy / Power^2

#### Throughput vs latency
- What is the code?
- What is the data set?
- What are the execution conditions?
- What is the metric?
- What is the baseline?
	- Normalized vs Absolute

#### Static vs Dynamic Instruction Count
- Static: # of instructions at compile time, at face value, the amount of lines of instructions in the instruction memory, in the program.
- Dynamic: # of instructions at run time, the amount you end up executing, this take in account of loops, conditionals, controls, but that also means you don't count some exceptions, some branches.

#### Workload
Workload = Program + Input/Data Set + Execution Conditions + Metric

- Same code, different data behaves differently
	- What if a loop depends on input, and output wildly varies then
- Input affects cache, memory, branches, parallelism
- Benchmarks must define both code and data

## Benchmarks

### Early Benchmarks

#### Whetstone
- Early floating-point benchmark
- Modeled Scientific Computation
- Focused on heavy arithmetic
- Synthetic and limited realism

#### Dhrystone
- Integer-oriented benchmark
- Focused on control flow and memory operations
- Easy to run and widely used
- Highly sensitive to compiler optimizations
- could be gamed

### SPEC Benchmarks
- Standard Performance Evaluation Corporation
- More realistic workloads
- Defined inputs and measurement rules
- Allowed fair comparison across systems

#### SPEC Evolution
bunch of more shit
- Updated to reflect modern workloads
- Older stuff is shittier bc less representative

#### PARSEC
- for multi-core
- parallel apps and shared memory workloads
- focused on scalability and contention


#### MLPerf
- more stuff with domain

There's no more modern standard benchmarks anymore

### Synchronous vs Asynchronous Design
#### Synchronous
- Uses a global clock
- state updates at clock edges
- predictable timing, easier design
- most widely used
#### Asynchronous
- no global clock
- uses handshaking between components
- potential for lower power and faster average case
- harder to design and verify