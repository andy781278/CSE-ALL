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

writer {
	w_or_r.decr(); //locks out readers
	Write;
	w_or_r.incr(); //up for grabs
}

reader{
	mutex.decr(); //locks readcount
	readcount++; // 1 more reader
	if (readcount==1) { 
		w_or_r.decr(); // sync with writers
	}
	mutex.incr(); // unlock readcount
	Read;
	mutex.decr(); // lock readcount
	readcount--; // 1 less reader
	if(readcount==0){
		w_or_r.incr(); // up for grabs
	}
	mutex.incr(); // unlock readcount
}
```

If the int is 0, things trying to `decr` it will be stuck until it gets higher?
`w_or_r` coordinates between readers or writers, `decr` on it makes it 0, and makes it unavailable for the other class until you are done.
`mutex` locks readcount since other readers will see mutex decrease but it's at 0, so it gets stuck?

#### Bounded Buffer Problem
- there is a set of resource buffers shared by producer and consumer threads
	- Producer inserts resource into buffer set
	- consumer removes resource from the buffer set
- producer and consumer execute at different rates
	- no serialization of one behind another
	- task are independent and decoupled
	- buffer set allows each to run without explicit handoff
- Safety
	- seq of consumed values is prefix of seq of produced values

- Invariants
	- $0 \leq \# p - \# c \leq N$ - produced never more than N
	- $0 \leq (\# c - \# p) + N \leq N$ - consumed never more than produced
- use three semaphores:
	- empty - count of empty buffers
	- full - count of full buffers
	- mutex - mutual exclusion to shared set of buffers

```
Semaphore mutex = 1;
Semaphore empty = N;
Semaphore full = 0;

producer{
	while (1) {
		Produce new resource;
		empty.decr(); // wait for empty buffer
		mutex.decr(); // lock buffer list
		Add resource to empty buffer;
		mutex.incr(); // unlock buffer list
		full.incr(); // note a full buffer
	}
}

consumer{
	while (1) {
		full.decr(); // wait for a full buffer
		mutex.decr(); // lock buffer
		Remove resource from a full buffer;
		mutex.incr(); // unlock buffer
		empty.incr(); // note empty buffer
		Consume resource;
	}
}
```


A possible downside to Semaphores is that a reaer won't know if the author intended for the Semaphore to be used as a binary or counting semaphore.