Scheduling is the decision making of which thread gets chosen from the ready queue and when, also which core on multi-core processors

Schedulable entities are usually called **jobs**

The Scheduler (dispatcher) is the module that manipulates the queues, moving jobs to and fro
- The scheduling algorithm determines which jobs are chosen to run next and what queues they wait on

In general, scheduler runs when
- a job switches from running to waiting
- interrupt occurs
- job is created or terminated

There are preemptive and non-preemptive systems, the preemptive ones can interrupt a running job, and non-preemptive can't, and have to wait for job to give it up themselves.

##### Scheduling Algorithm Goals
- Maximize CPU Utilization
- Maximize Job throughput (rate of completion)
- Minimize turnaround time (time for job to finish)
- Minimize waiting time (time each thread spends on wait queue before going on ready queue)
- Minimize response time (time each thread spends on ready queue before running)

Two types of systems:
Batch Systems - strive for job throughput and turnaround time (supercomputers)
Interactive Systems - strive to minimize response time for interactive jobs (PC)

We want to minimize **Starvation** - a process is prevented from working at all for a long time, just because it's not chosen by the scheduler
- Can be side effect of schedulers and synchronization techniques

## FCFS / FIFO
First come first serve
- Jobs are scheduled in order of arrival in ready Q, similar to real life lines
- No starvation, every job is treated equally, non-preemptive

What if there's a big ass job and a bunch of small ones?

## SJF
Shortest Job First
- choose the job with the smallest expected CPU burst, or takes shortest time / computational power
- optimal minimum turnaround time
- CPU usage is the same, time to compute is the same
- There is starvation
- It's also impossible to know the size of CPU burst, how?
	- make estimates?
	- look at past behavior?
- If we're being preemptive, we choose the shortest remaining job first, if we can estimate that is

## Priority Scheduling
Choose most important job first
- good finer control
- low priority jobs starve
- solution: age processes, where old processes have increased priority form just being old

## Round Robin
divide the time equally between all the jobs
- excellent for time sharing
- ready queue is circular
- each job is given a slice called a quantum
- the job executes for the duration and then is interrupted
- no starvation
- Context switches are frequent, need to be very fast or massive overhead


> [!tldr] Let's combine different algorithms
> Multiple level feedback queues (MLFQ)
> - Multiple queues for differnt job types
> - queues themselves have priorities, jobs on the same queue scheduled Round Robin
> - jobs can move among queues based on execution history, can increase prio on old jobs
> - Unix scheduler uses this
> - This mainly reduces response time, since short jobs can finish immediately before their quantum ends, good for user-interactive


