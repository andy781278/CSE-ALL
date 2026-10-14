FWhen we have multiple threads in the same process, they need to work together, share resources, access shared data structures, and coordinate their execution

For correctness we need to control this cooperation using synchronization to restrict the interweaving of thread executions that might cause bugs

The execution of threads is entirely dependent on the scheduler, so we have no direct control over the interweaving.

### Shared Resources
If two concurrent threads are accessing a shared variable, and that variable is read/modified/written by those threads, then access to the variable must be controlled to avoid errors

Example:
Withdraw from a bank account, 
```
withdraw (account, amount) {
	int balance = get_balance(account);
	balance -= amount;
	put_balance(account,balance);
	return balance
}
```
So if two people both withdraw $100 at the same time, context switch may happen between getting the new balance, and put_balance, so it's possible that put_balance is executed twice without an updated balance, therefore final balance in that account will be $900, even though two people both took out $100, only one of those were accurate, and the other overridden.

The problem is we have a shared resource (account) without synchronization, this is known as a **race condition**.

we need to sync every shared data structure. (queues, buffers, lists, hash tables, counters, even just an int or a bool)

From threads, we know that local variables are on the stack and are not shared, only the dynamic objects on the heap, static data, and code is shared.

context switch can happen between any two instructions, so you can, at worst case scenario, get 1 line per thread before a context switch. Luckily, we can delay a thread for as long as it's not forever.

We use **Mutual Exclusion**, which means only one thread in a process can access a shared resource at a time.

The part of code that uses mutual exclusion is called a **Critical Section**, which means only one thread can execute that part of code at a time, and when they're done, the next one can come in and execute that section.

