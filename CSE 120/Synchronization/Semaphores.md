A high level mechanism to provide protection of critical sections so we can do synchronization stuff. Higher level than locks. These, including Monitors, also include the functionality of threads running relative to each other.

All OSes implement Semaphores.

Semaphores are atomic counters, integers that support two operations:

`Semaphore.P()`: decrement

`Semaphore.V()`: increment

We cannot access the value, we can only call P or V to decrement or increment.