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

