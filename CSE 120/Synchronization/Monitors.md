A monitor is a programming language construct that controls access to shared data
- Synchronization code added by compiler enforced at runtime

A monitor is a module that encapsulates
- shared data structures
- procedures that operate on the shared data structures
- synchronization between concurrent threads that invoke the procedures

A monitor protects its data from unstructured access, it guaranteed that thread accessing its data through tis procedures interact only in legitimate ways


A monitor guarantees mutual exclusion through the compiler, so programmer can forget about it
- only 1 thread can execute any monitor procedure at any time, the thread is in the monitor
- if a 2nd thread invokes a monitor procedure when the 1st thread is already executing one, it blocks, the monitor has a lock with a wait queue
- If a thread within a monitor blocks, another one can enter


> [!info] Basically, a monitor is a class with a single lock, and all methods in that class competes for that single lock for all of its threads, no matter how many methods.


Monitors have condition variables that support three operations on the variables:
- Wait - releases monitor lock, sleep, reacquire lock when woken sometime in the future by the same variable with signal or broadcast
- Signal - wake up a waiting thread that used the same variable's wait function to wait
- Broadcast - wake up all waiting threads of that variable

We cannot ask if this variable is true, because it is not a Boolean object.



> [!info] Wait Queues
> - There are 1 wait queues for each condition variable, and 1 for the entire monitor object
> - A thread can be waiting on a condition variable after it calls wait on that variable, and then we some other thread calls signal, it leaves the wait queue of that variable and joins the wait queue of the main monitor lock
> - When it moves up the monitor lock and gets picked, it can resume doing shit


### Reader Writers Problem
```
Monitor rwLock {
	int nr=0,nw=0;
	Condition canRead, canWrite;
	
	void acquireRead() {
		while (nw!=0) do canRead.wait();
		nr++;
	}
	
	void releaseRead() {
		if (nr==0) canWrite.signal();
	}
	
	void acquireWrite() {
		while (nr != 0 || nw != 0 ) do canWrite.wait();
	}
	
	void releaseWrite() {
		nw--;
		canRead.broadcast();
		canWrite.signal();
	}
}
```

A monitor anatomically, is just a condition variable and a lock in a module/object. We can create it without using explicitly a monitor, and it's the same, as long as we put acquire() on entry and release() on exit

Implicitly, most languages has this built into every variable, and also into the compiler, so you can fine tune if necessary, but don't have to worry otherwise.