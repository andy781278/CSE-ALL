![[Pasted image 20261110230229.png]]
Solves the external fragmentation problem by using fixed-sized units for physical and virtual memory
- Pages are scattered throughout physical memory, with virtual pages mapped to physical pages
- The mapping is invisible to the process
- A process literally cannot reference memory outside of its VAS, so it's protection

![[Pasted image 20261110230700.png]]
Translating addresses
- Virtual address has two parts: virtual page number and offset
- VPN is an index into a page table
- Page table determines page frame number (PFN)
- Physical address is PFN::offset (concatenate)

Page tables
- Map virtual page number (VPN) to page frame number (PFN)
- VPN is the index into the table that determines PFN
- PFN is also physical page number
- One page table entry PTE per page in virtual address space

Example:
- Virtual address = 0x7468
- Split into two: 0x7 and 468
- 0x7 -> page table -> 0x2
- 0x2 + 468 = 0x2468


Page Table Entries (PTE)
![[Pasted image 20261110230858.png]]
Modify bit says whether or not the page has been written
Reference bit says whether the page has bee naccessed
Valid bit says whether or not the PTE can be used
Protection bits says what operations are allowed on the page (read, write, execute)
- PTE for page 0 is no-read, no-write, and no-execute
PFN determines physical pages

### Advantages
- Easy to allocate memory
	- it is completely arbitrary, a virtual page does not care which physical page it uses
	- memory comes from a list of fixed-sized chunks
	- allocating a page is just removing from the list
	- external fragmentations not a problem
- Easy to swap out chunks of aprogram
	- All chunks same size
	- use valid bit to detect references to swapped pages
	- pagers are convinent multiple of the disk block size

### Limitations
- Can still have internal fragmentation when processes don't use memory in multiples of a page
- Memory reference overhead, 2 refences per address lookup
	- Use hardware cache of lookups

### Memory requires to hold page table can be very massive
- only need to map the portion of the address space actually being used (a fraction of the entire addr space)
- Can dynamically extend page table, does not work if addr space is sparce (internal fragmentation)
- use two-level page tables

### Two-Level Page Tables
Virtual Addresses have three parts:
- Root page (only 1 root page)
	- Maps to secondary page table
- Secondary page (many)
	- Maps to physical page
- Offset
	- Indicate where in physical page address is located
![[Pasted image 20261110232636.png]]

Every address space that is on the page table is mapped, so there are unmapped virtual addresses.

Heap is the only region that can dynamically grow when running via malloc or new
- Processes can ask the OS to grow their heap
- brk/sbrk: sys call to change heap boundary, malloc lib calls it when running out of heap space
- brk allocates more ptes in the page table


### Page Table Storage
Wait, where do we store the page tables themselves? Let's put it in the OS's address space, since it's sort of OS territory. Let's put it in the virtual address space of the OS.

Wait, where is that? How does OS virtual address space work?
![[Pasted image 20261110233634.png]]
It's actually above the usual virtual address space, and it is there for every virtual address space of every process, but it's only accessible in kernel mode, not for average chums.

Reason is so that the OS won't have to care which user app called for its help, since virtual address space is all the same in all the processes anyways.

### Efficient Translations
But uh oh, using two-level page tables triples the cost because you have to look into the page table, and look again, then fetch the data. 64-bit architectures does 4+ level page tables with even more cost.

How do we use paging without translation overhead?

#### TLB
Translation Lookaside Buffer, translates virtual page numbers to PTEs
a cache of recently used page table entries, relatively small storage
But since recently used pages are more likely to be used again, we hit things on the TLB often
![[Pasted image 20261111001834.png]]

Who loads the TLB?
Hardware
- Knows where page tables are in main memory
- OS maintains tables, HW accesses them directly
- tables have to be in HW-defined format (inflexible)
Software (OS)
- TLB faults to the OS, OS finds appropriate PTE, loads it.
- Must be fast
- tables can be in any format convenient for OS (flexible)
- Ensures TLB and page tables are consistent


Reload TLB on a process context switch, which invalidates all entries, causes overhead to fill it again

When TLB misses and a new PTE loads, it kicks a PTE in the cache, implemented in hardware

## Demand Paging
![[Pasted image 20261111002933.png]]
A process only needs a subset of its virtual pages loaded, the rest can be just chillin in disk. On demand, it loads from disk to CPU
- As memory fills up, allocating a page requires another existing one to be evicted, which puts them back to disk.
- You can put them back to their corresponding file if you are using a file system.
- All done by OS