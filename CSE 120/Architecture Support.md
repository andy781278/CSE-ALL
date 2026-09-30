Hardware support that helps the OS, there's three big genres of support:
## Privileged Instructions
A subset of instructions of every CPU that is strictly for OS use
- Directly access I/O devices like disks, printers, for security and fairness
- Manipulate memory management state
- Manipulate protected control registers
- Halt instructions (protect against other users)
Usually the ISA describes which instructions are privileged

In order for the CPU to know whether the OS or the user is trying to execute the instruction, the architecture have to have two modes: Kernel mode and User mode
- Privileged instructions only execute in kernel mode
- user programs execute in user mode
- OS executes in kernel
- mode is indicated by a bit in a protected control register
- CPU checks the bit to see if the privileged instruction is allowed to execute, the OS is not allowed to check
- The operation to change the mode bit is also privileged

## Memory Protection
OS needs to protect programs from each other and protect itself from user programs, but it doesn't protect user programs from itself.
- Page table pointers, page protections, segmentation, TLB, are all hardware supports for memory protection
- Manipulating memory management hardware uses privileged/protected operations

## Events
events are unnatural change in control flow that the CPU doesn't know what to do
- upon an event, CPU immediately stops current execution, changes mode / context
- The OS defines a handler for each type of event, well defined
- event handlers are always executed in kernel mode
- In a broader sense, the OS is just one big event handler
	- OS and user programs can't run together, since the CPU can only focus on one task at a time, with one mode at a time
	- so OS only runs when events fire and user programs are not in play

There are two types of events:
##### Interrupts
Caused by external event like device finishes I/O, timer expires
Analogy: receiving a phone call, text message
##### Exceptions
Caused by executing instructions, CPU requires software intervention to handle a fault or trap
Analogy: divide by 0
We then take all the current state of the CPU and saves it to memory, then we transfer control to OS in a context switch. After the system handler handles the event, the memory is used to load everything back to how it was, and resume instructions.

Events can be Unexpected or Deliberate
- deliberate events are thrown in order for user apps to ask the OS to work for them

### System Calls
For when a user wants to do something privileged, it must call an OS procedure.
- crossing the protection boundary, protected procedure call, protected control transfer
- CPU ISA provides a sys call instruction that
	- causes an exception, goes to kernel handler
	- passes parameter determining system routine to call
	- saves caller state
	- changes user to kernel
	- then after stuff is done, goes back to the program and restores everything
- ARM: SVC (supervisor call)
- x86: INT (interruption)

## Faults
Similar to exceptions, hardware can detect and report exceptional conditions like page fault (different fault), unaligned access, divide by zero.
- Upon exception, hardware faults
- they save state, so it is sort of paused and stored away, can be used later

Faults are not necessarily bad, they can be used deliberately for debugging, garbage collection, performance optimization

#### Handling Faults
When faults are generated, and user program exits, and hands control back to OS, the OS runs an event handler to handle the events, they have several options:
- Fix the exceptional condition and returning to the faulting context
	- Page faults can have OS bring the page into memory
	- Fault handler resets PC of faulting context to re-execute instruction that caused the page fault
- If the user program already has their own handler, they will delegate it to the program instead.
	- The handler must be registered with the OS
	- the handler is not as strong as the OS, they can't do as much things, only things the OS allows
	- The user handler can be shit, and the OS can't do anything about it, so its possible to get stuck in an infinite loop where the handler gets called and doesn't fix the problem every time
- Terminate unrecoverable faults by killing the user application process
	- default action for many signals
	- when this happens in the kernel, the OS crashes
		- dereference null, divide by zero, undefined instruction
		- blue screen of death

Hardware handlers delegate to user program handlers, and programming languages can delegate these handlers to user written code.

