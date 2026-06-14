A small fast memory that behaves/acts like a much larger memory. The Cache is essentially a small copy of the main memory, so that it takes less time for CPU to get what it needs.

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

### Cache Anatomy
Essentially, with a software scope, a cache is a lookup table with a key value pairing. The key is the memory address decomposed into the tag, and index, and offset, and the value is the value corresponding to the memory address, if it's been found. If it's not, then it will be pulled along with some neighbors in a big block from the main memory into the cache, possibly replacing others in chunks or blocks or lines, but always a block at a time, nothing less, nothing more.

### Load Cache Designs
Since caches are smaller, it's a hashing problem to map the big memory to the small one. There are possible collisions, when multiple addresses hit the same space in the cache. Those issues have to be resolved in 1 cycle.

> [!info] Address Decomposition
> The size of the offset, index, and tag depends on the length of the memory address, as well as cache design, basically, it's up to you. Here's some rules:
> - $\text{Offset Length} = log_2 (\text{Block Size})$, so you can pinpoint the data from within the cache line/block
> - $\text{Index Length} = log_2 (\text{Number of Lines/Blocks})$, so you can find which block/line potentially has your data
> - $Tag$ is used for verification, to see if your block is the same as the one from memory that has your data.
> - Address = A bits total
> - Cache size = C bytes
> - Block size = B bytes
> - Ways = N

There are three types of caches, each with a different strategy to handle the issue.
#### Direct Map
Each memory address has a specific corresponding cache block, this makes it easy to find data, but multiple data can fight over the same block.

`S=C/B, which means Index length is log2(cache size / block size)`
`[ Tag | Index | Offset ]`
`A - (index + offset) bits | log₂(S) bits | log₂(B) bits`

#### Fully Associative
Any address can go in any slot, which makes it easier to pull data into the cache without conflicts, but finding that data means checking every block, which is expensive. No index, only Offset and Tag.

`[ Tag | Offset ]`
`A - offset bits | log₂(B) bits`
#### Set Associative
A middle ground between direct map and fully associative. The cache is divided up into sets, and the index is used to find which set to look in, then the hardware scans all data in that set in parallel, since it's hardwired number of data per set, we don't have to check sequentially.

The number of sets is S, which is gotten by $S=\frac{C}{BN}$, where C is cache size, B is block size, and N is number of ways.

So as the number of ways increase, S, or the number of sets decrease, it's inverse.

| Method                    | # of sets | # of ways |
| ------------------------- | --------- | --------- |
| Direct Map                | 8         | 1         |
| 2 way                     | 4         | 2         |
| 4 way                     | 2         | 4         |
| 8 way (Fully Associative) | 1         | 8         |

`[ Tag | Index | Offset ]`
`A - (index + offset) bits | log₂(S) bits | log₂(B) bits`

### Cache Performance
$MCPI=\text{Base CPI}+ \text{(Instruction Cache Miss Rate + Data Cache Miss Rate) * Miss Penalty}$
$MCPI=\text{Base CPI + (Memory Accesses/instruction * Miss rate * Miss penalty)}$

![[Pasted image 20260529192659.png]]

#### Cache Block / Line
16-256 words/bytes

When retrieving data from bigger memory, we retrieve it in blocks/lines.

### Writing with caches
- Hitting
	- Write back
		- Writes only into cache, and make the block dirty
		- This way, multiple writes can be performed on that block before it's put back into main memory, saving a lot of time
		- When you need to replace a dirty block, you first write it back into main memory
	- Write through
		- Writes directly into cache and main memory
- Missing
	- Write Allocate
		- brings the block into the cache before performing write
		- useful if you know you'll need that segment again
	- Write around
		- Goes around the cache and writes directly into main memory
		- useful for if you know you won't need that again
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

