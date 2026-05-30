A small fast memory that behaves/acts like a much larger memory. The Cache is essentially a small copy of the main memory, so that it takes less time for CPU to get what it needs.

Since caches are smaller, it's a hashing problem to map the big memory to the small one.

There are possible collisions, when multiple addresses hit the same space in the cache. Those issues have to be resolved in 1 cycle.

**Cache Hit** - Success, data is in cache when asked

**Cache Miss** - Fail, data is not in cache when asked

**Hit time** - time to access the cache and hit

**Miss penalty** - time to move data from further levels to closer

**Hit ratio** - percentage of time data is found in cache

**Miss ratio** - 1 - hit ratio

**Cache block size / cache line size** - amount of data transferred on a data miss

**Instruction cache** - cache that only holds instructions, separate from data cache, usually in 1st level. Other levels are unified

**Data cache** - Cache that only holds data

**Unified Cache** - has both Data and Instructions

![[Pasted image 20260529192659.png]]

#### Cache Block / Line
16-256 words/bytes

When retrieving data from bigger memory, we retrieve it in blocks/lines.

### Writing with caches
- Hitting
	- Write back
	- Write through
- Missing
	- Write Allocate
	- Write no Allocate

In real life, there are two bottlenecks that needs to be solved

- Memory Latency Wall
	- Memory takes a long time (~500 cycles) to retrieve
- Bandwidth Wall
	- too little data retrieved at once.

Solution:
Let's create a mini ram inside the CPU, so we can access memory faster.
Let's call it a **Cache**
- The software side cannot know about this, to them, memory is just a single box.

### Memory Triangle
![[Pasted image 20260529184531.png]]
You cannot have all 3, you can have at most 2.


### Memory Locality
Future memory accesses are near past accesses
- Temporal Locality
	- Near in time, we will need the same data again soon
- Spatial Locality
	- our next access is often very close to our last one

### Hierarchy of Memory
- SRam
	- Cache, most powerful, in chip
	- stores data in a loop of 2 not gates
	- 3 levels of caches,  each bigger and slower than the previous one
- DRam
	- Memory
	- stores data in a capacitor, periodically refills them because they leak, this makes them dynamic, hence the D
	- DDR
		- Double data rate, transfers data on rising and falling edges
	- QDR
		- Quad data rate, separate DDR inputs and outputs
- Disk
	- Big and slow

