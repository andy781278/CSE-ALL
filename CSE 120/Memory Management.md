- To provide a convenient abstraction for programming
- To allocate scarce memory resources among competing processes to maximize performance with minimal overhead

### Virtual Memory
- VM enables a program to execute with less than its complete data in physical memory
- Many programs do not need all of their code and data at once, so there's no need to allocate physical memory for it
- OS will adjust amount of physical memory allocated to a process based upon its behavior
- Requires hardware support and OS management algorithm


Mainly bc of multiprogramming (multiple programs running at once)
- Need protection - restrict which addresses jobs can use
- Fast translation - lookups need to be fast
- Fast change - updating memory hardware on context switch



### Virtual Addresses
Independent of physical location of data references, not tied to it, leave it all to the OS. OS helps translate virtual to physical and vise versa.
A process' virtual address space (VAS) stores its virtual addresses. Often larger than physical memory, but can also be smaller


# Fixed Partitions
![[Pasted image 20261110225640.png]]
Physical memory is broken up into fixed partitions
- Physical address = virtual address + base register
- Base register is loaded by the OS when it switches into a process
- size of each partition is same and fixed

Easy to implement, fast context switch

Problems
- Internal fragmentation: memory in a partition not used by a process is not available to other processes
- Partition size: one size does not fit all (very large processes)



# Variable Partitions
![[Pasted image 20261110225912.png]]
Natural extension - physical memory is broken up into variable sized partitions
- Physical address = virtual address + base register
- If (physical address > base + limit) then fault

No internal fragmentation: allocate just enough for process

Problems
- External fragmentation: process creation and termination produces empty holes scattered throughout memory

![[Paging]]
# Segmentation
Partitions memory into logically related data units. Regular partitions like Code, Stack, Heap, Static Data, are all separate segments
- module, procedure, stack ,data, file, etc
- Virtual addresses become <segment #, offset>
- Natural extension of variable-sized partitions
	- Variable-sized partitions: 1 segment/process
	- Segmentation = many segments/process
![[Pasted image 20261110231924.png]]
![[Pasted image 20261110231928.png]]

