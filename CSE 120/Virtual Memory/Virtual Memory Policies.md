Paging schemes depend on locality

Temporal Locality
- Locations referenced recently are likely to be referenced again
Spatial Locality
- Locations referenced near other referenced locations are likely to be referenced soon

Although paging is demanding, the locality cancels that down side and makes it worth

Dirty pages are modified, and will need to be pushed back to disk, but clean ones are identical to the ones on disk, so no need to push back, but you do need to know where it's at so you can pull again when it's outdated

### Demand Paging
When a process first starts up, it's empty of pages, then page faults start asking for pages required, which is loaded one by one until it's satisfactory.
- This is done via valid bits, a new page table with all valid bits off
- Instruction faults on code and data pages
- At all times only pages needed are loaded

### Page Replacement
How do we choose which page to replace when the cache is full?

#### Belady's Algorithm
Choose the page that is most likely to never be touched again.
That's hard to tell, so you can choose the page that is likely to be used the latest time in the future

Belady's Algorithm is known as the optimal page replacement algorithm because it has the lowest fault rate for any page reference stream

#### First-In First-Out (FIFO) (Queue)
Keep pages in an ordered list, evict the oldest one
- Maybe the oldest ones won't need to be used anymore
- We don't have info to say one way or the other though
- Suffer from Belady's Anomaly, fault rate might increase when algorithm is given more memory (Very Bad)

#### Least Recently Used (LRU)
Use references information to make a more informed replacement decision. On replacement, evict the page that has not been touched for the longest time in the past
- To be perfect, need to timestamp every reference, too costly
- Need approximate it
	- Use PTE reference/used bit
	- keep a counter for each page
	- At regular intervals, for each page, do:
		- If ref bit = 0, increment counter
		- If ref bit = 1, zero the counter
		- Zero the reference bit
	- The counter will contain the number of intervals since last reference
	- Choose the page with the largest counter

#### Not Recently Use (NRU)
Arrange physical page frames in a big circle (clock)
- A clock hand selects a good LRU candidate
	- Sweep through the pages in circular order like a clock
	- if the ref bit is off, then it hasn't been used recently
	- If it is on, turn it off and go to next page
- Arm moves quickly when pages are needed
- Low overhead when plenty of memory
- If memory is large, accuracy of information degrades
	- But you can use two hands, leading erase hand, trailing select hand
	- Hands have a fixed angle and moves at the same time

### Reduce Page Fault Time
We can't grab free physical pages while we're evicting, that will take too long. Instead, keep a list of free physical pages, and grab any when you need it.

Do it in the background, off the page fault critical path.
- Page/swap daemon runs occasionally, executing the page replacement algorithm
- When list reaches a low water mark, run daemon
- When list reaches a high water mark, stop
- Enables daemon to evict many dirty pages at once to amortize

Let's give the free physical pages a second chance while they're in the free list but haven't been reallocated yet. We'll rescue it from the free list and give it back to the process


### Allocate memory to programs
When multiple processes want memory, we need to allocate properly
Fixed space algorithms
- Everyone has equal memory, a limit of pages it can use
- When it reaches limit, replaces from its own pages
- Local replacement
Variable space algorithms
- Process' set of pages grows and shrinks dynamically
- Global replacement

#### Working Set Model
A working set of a process is used to model the dynamic locality of its memory usage
- $WS(t,w)=$ {page P such that P was references in the time interval (t,t-w)}
- w is working set window, measured in page references
- A page is in the working set only if it was references in the last w references

The size of the working set is the number of unique pages in the working set
- changes with program locality
- Poorly locality reference more pages, larger working set size

Generally, you want the set to contain the pages a process needs to not heavily fault all the time, basically all the pages it needs to work

This model is fine as a concept, but hard to implement. We need to know a process' working set size, the number of pages it needs to work.


#### Page Fault Frequency (PFF)
variable space algorithm that uses a more ad-hoc approach
- Monitor fault rate for each process
- If above threshold, give it more memory so that it faults less
- If below threshold, take away memory
Hard for PFF to distinguish between changes in locality and changes in size of working set

#### Thrashing
When most of the time spent by OS in paging data back and forth from disk, and little time doing actual useful work.
Need to avoid for page replacement algorithms. 
System is overcommitted
- No idea which page should be in memory to reduce faults
- could just be that there isn't enough physical memory for all of the processes in the system
- You can swap out all of the pages of a process, or buy more memory

