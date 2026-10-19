A high level mechanism to provide protection of critical sections so we can do synchronization stuff. Higher level than locks. These, including Monitors, also include the functionality of threads running relative to each other.

All OSes implement Semaphores.

Semaphores are atomic counters, integers that support two operations:

`Semaphore.P()`: decrement
- Block until semaphore is open
- If semaphore is open, thread continues
- If semaphore is closed, thread blocks on a wait queue

`Semaphore.V()`: increment
- allow another thread to enter
- If a thread is waiting on the queue, the thread is unblocked
- If no threads on the queue, the increment is remembered by the next thread

We cannot access the value, we can only call P or V to decrement or increment.

Two types of semaphores:

##### Binary (mutex) (mutual exclusion)
- Only goes 0 or 1
- represents single access to a resource
- guarantees mutual exclusion to a critical section

##### Counting (general)
- arbitrary value depend on application
- Represents a resource with many units available, or a resource allows certain kinds of unsynchronized concurrent access
- multiple threads can pass the semaphore
- number of threads determined by the semaphore "count", which for Binary is 1.

### Implementation

Similar to locks
```
struct Semaphore {
	int value;
	Queue q;
}

withdraw(account, amount) {
	decrement(S);
	do critical section;
	increment(S);
	return balance;
}
```


### Example Problems

#### Readers Writers Problem
- An obj is shared among several threads
- Some threads only read the obj, others only write it.
- We can allow multiple readers but only 1 writer
	- Let #r be the number of readers, #w be the number of writers
	- Safety: $(\#r \geq 0) \wedge (0 \leq \#w \leq 1) \wedge \big((\#r > 0) \rightarrow (\#w = 0)\big)$
	- 0 or more readers, 0 or 1 writer, and no simultaneous readers and writers
- How can we use semaphores to control access to the obj to implement this protocol?
- Use three variables
	- int `readcount` - number of threads reading object
	- Semaphore `mutex` - control access to readcount
	- Semaphore `w_or_r` - exclusive writing or reading

```
int readcount = 0;
Semaphore mutex = 1;
Semaphore w_or_r = 1;
```