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

#### Spinlock
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
- prevents context switches