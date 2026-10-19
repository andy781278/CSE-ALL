A lock is an object in memory providing two operations:
- `acquire()` to enter a critical section
- `release()` to leave a critical section

Thread pair calls to acquire and release
- between acquire/release, the thread holds the block
- acquire does not return until any previous holder releases

The lock is shared by all threads and lives in the heap of the process

However, deadlocks happen often, where the calls are not paired
Issues
- If you acquire a lock and never release it, no other threads can ever enter the critical section.
- If you forget to call acquire, multiple threads can enter the critical section at once

## Spinlock
Simple lock implementation
```
struct lock { int held = 0; }

void acquire(lock) {
	while (lock -> held) {
		lock -> held = 1;
	}
}

void release(lock) {
	lock -> held = 0;
}
```
The thread who acquires the lock spins it continuously in the while loop, making the lock's held 1 continuously.
When release is called, the loop stops, and others can now acquire.

Issue: When context switch happens between while line and lock -> held = 1 line, more than 1 thread can acquire. This is because the implementation has critical sections too.

Two solution approaches:

### Atomic Instructions
- The implementation of acquire/release must be **atomic**, which means it executes "all or nothing"
- User level instructions that executes all at once, with no interrupts or context switching allowed, it is all treated as a single instruction. Context switching can happen before or after, not in between
- Test-And-Set
	- Record old value
	- Set value to true
	- return old value
- This will be treated as a single instruction, even though there are three

```
struct lock { int held = 0; }

void acquire(lock) {
	while (test-and-set(&lock->held));
}

void release(lock) {
	lock -> held = 0;
}
```


### Disable/Restore Interrupts
- prevents context switches and interrupts
```
struct lock { int held = 0; }

void acquire(lock) {
	disable interrupts;
}

void release(lock) {
	restore interrupts;
}
```
- There is no state associated with the lock
- However, this stops external I/O from working, since that triggers a context switch, something like a timer or a keyboard press
- in a real system, this only available in kernel
- disabling interrupts is insufficient on a multiprocessor since interrupts are only disabled per core, so if that one disables interrupt, then another one can just do it
- We only want to use disable interrupts to implement higher level synchronization primitives

### Block Waiters
Let's disable interrupts on acquire and release, and just have it enabled on the critical section, but we will sleep all threads that needs the critical section to run until the lock is released, then the queue is waken up. It will not be scheduled again while it's asleep.
```
struct lock {
	int held = 0;
	queue Q;
}

void acquire(lock) {
	Disable interrupts;
	while (lock->held) {
		put current thread on lock Q;
		sleep current thread;
	}
	Enable Interrupts;
}

void release(lock) {
	Disable Interrupts;
	If (Q) {removes waiting thread;}
	ready waiting thread;
	lock->held = 0;
	Enable Interrupts;
}
```


OSes are very sensitive to overhead of locking, it stalls a lot, so we want to minimize the stalling and optimize
- test-and-test-and-set
- test-and-yield
- test-and-sleep
- many others


