Threads are a sequential execution stream within a process, which consists of PC, SP, and registers

processes defines the address space and general process attributes, everything but threads of execution

A thread is bound to their single process

Threads are the basic unit of scheduling, processes become static containers from which threads reside within.

![[Pasted image 20261014000710.png]]

Each thread has their own stack, but they share code, heap, and other static data.

Using threads makes it much cheaper/efficient for multithreaded applications, even on a single core processor

The OS now operates on processes and threads. Thread operations are implemented in the kernel

OS managed threads are called kernel-level threads or lightweight processes

![[Pasted image 20261014132803.png]]

Whenever the thread makes a sys call, the OS adds it into its kernel stack and let it operate inside the OS using the kernel stack.

![[Pasted image 20261014133010.png]]

Each kernel makes a separate kernel stack in the OS when making a sys call, they can all work in parallel. Allows OS to use parallelism in its favor.

However, sys calls are more expensive than regular procedure calls, so we shouldn't need to use that every time.

So we make User-level threads, which are managed by the run-time system, or the user level

User-level threads are small and fast
- a thread is just a PC, registers, stack, and a control block TCB
- creating a new thread switching between threads, and syncing them are done via procedure calls
- user level operations are 100x faster than kernel threads

Downsides:
- not integrated with the OS, so can't use them for physical parallelism

So we use both kernel and user level threads

### Implementing Threads

KThread.fork - starts a thread, marks itself ready, and puts itself on the ready queue
KThread.sleep - blocks a thread from running
KThread.ready - start the given thread
KThread.yield - voluntarily give up the processor, puts self back to end of ready queue
KThread.join - Block until another thread finishes, join blocks the caller until itself finishes, by then it would place the caller in the back of the ready queue
KThread.finish - terminate the calling thread

#### Thread Scheduling
We keep a thread scheduler to determine when which thread runs, we keep track of 3 queues:
- Run Queue: Threads currently running
- Ready Queue: Threads ready to run
- Wait Queue: Threads blocked or asleep waiting

#### Non-Preemptive Scheduling
Threads voluntarily give up the CPU with yield

Yield - gives up the CPU to another thread, context switches, when a yield returns, it means another thread called yield, and it came back to this one.

![[Pasted image 20261014140557.png]]
puts thread in ready queue, then context switches, then waits for prio to come back to it, then runs again as the "new" thread.

#### Preemptive Scheduling
Uses timers interrupts, when timer fires, it forces the thread to call yield. Whether as the non-preemtpive threads must voluntarily give up the CPU, the preemptive ones can be taken away from it without consent.

