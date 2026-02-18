void* malloc(size_t **size**)

sets aside **size** bytes on the heap and returns the address of the start of that space

returns NULL if there is no more space in the heap (crash likely)

#### How does it work
On the memory block, at some point
- HEAP_START pointer points to the start of the heap.
- HEAP_END pointer points to the end of the heap.

Key Idea: On each malloc() or free(), we store metadata about allocations.
- We also need to put that on the heap, cause where else are we gonna put it lol, it's dynamic spacing
- malloc() will create blocks on the heap
	- each block will have a special first 8 bytes called "header"
	- Header stores:
		- block size
		- if block is free / allocated
	- How header stores metadata:
		- header stores the size of the block, which comes in 8 byte increments, so the first 3 bits (1,2,4) are not used.
		- sizes is a 64-bit unsigned number
		- So we use the LSB and have it be the free bit, 1 for busy, 0 for free.
	- malloc then returns the address of the first space after the header as a pointer

- malloc stores data in 8 byte chunks
	- If you put in non-8 byte multiples, then it rounds up to the nearest multiple of 8
	- then you add 1 in the header for the LSB being 1 (busy)

