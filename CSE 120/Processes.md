> [!faq] Why Processes are Important
> OS creates an abstraction for the CPU, so users/programmers only interact with the abstraction, not the CPU
> Processes are a key fundamental concept for this.
> The only way to run a program through an OS is through a process

The Process is the OS abstraction for **execution**
- It is the unit of executing
- It is the unit of scheduling
- It is the dynamic execution context of a programs

Also called a Job, Task, or Sequential Process

A process is a program in execution
- It defines the instruction-at-a-time execution of a program
- programs are static entities with the potential for **execution**


Under the covers, the process is a data structure, it stores these things that encapsulate all state for a program in execution:
- address space
- program code
- program data
- execution stack encapsulating the state of procedure calls
- program PC
- set of general-purpose registers with current values
- set of OS resources that's used by the program

> [!info] A program has a unique identifier: **PID** (process ID)

Every process has an address space
![[Pasted image 20261006204156.png]]


A process has a **state**:
- Running: executing instructions on the CPU
- Ready: Waiting to be assigned to CPU
- Sleeping: Waiting for an event like I/O completion
As a process executes, it moves from state to state
One core can have one process running on it at once

![[Pasted image 20261006205238.png]]

## Process Control Block
Big Data structure that encapsulates a process
- PID
- Process State
- Hardware State (PC, SP, general registers)
- Memory Management
- Scheduling
- Accounting
- Pointers for process sate queues
- Etc.
- It is a heavyweight abstraction

When the process is running, its hardware state (PC, SP, regs, etc.) is in the CPU. The hardware registers contains the current values
- When the OS stops running a process, it saves current states into PCB
- When OS is ready to execute a new process, it loads the hardware regs from the values stored in the PCB
- The steps of changing the CPU hardware state from one process to another is called a context switch.

## State Queues
queues are used to track processes, one queue for each process state out of ready, sleeping, etc.
Each PCB is queued on a state, and they can be unlinked from one and into another

## Process Creation
The only way to create a process is to have another process create it, Parent creates Child process
- The first process is created by the OS itself
- The child takes the User ID of the parent process
- The parent determines privileges of the child


> [!info] Process Creation in Windows
> `CreateProcess(char *prog, char *args)`
> - Creates and inits new PCB
> - Creates and inits new address space
> - loads program specified by "prog" into the address space
> - copies args into memory allocated in address space
> - inits the saved hardware context to start execution at main
> - places the PCB on the ready queue


> [!info] Process Creation in UNIX
> `fork()`
> - creates and inits a new PCB
> - creates new address space
> - inits address sapce with a copy of the entire contents of the address space of the parent
> - inits the kernel resources to point to the resources used by parent
> - places the PCB on the ready queue
> 
> This makes fork return twice
> Returns the child's PID to the parent, 0 to the child
> 
> Next, they call
> `exec(char *prog, char* argv[])`
> - Stops current process
> - loads prog into process address space
> - inits hardware context and args for the new program
> - places the PCB onto the ready queue
> - it does not create a new process
> - exec can return error

## Process Termination
Unix: `exit(int status)`, Windows: `ExitProcess(int status)`
Free resources and terminate
- terminate all threads
- close open files and network connections
- free allocated memory
- remove PCB from kernel data structure and free

The OS has to do it, the process can't clean up itself


Sometimes it might be worth for the parent to wait() until the child process has finished
- Think of executing commands in a shell
- Unit: `wait()`, Windows: `WaitForSingleObject()`
- you can also use `wiatpid()` to wait for a specific child process to end
- wait returns exit value to parent, so child can communicate how it terminated