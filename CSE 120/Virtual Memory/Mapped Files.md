Mapped Files allows processes to do file I/O using loads and stores instead of open, read into buffer, operate on buffer.

Bind a file to a virtual memory region (mmap() in Unix)
- PTEs map virtual addresses to physical frames holding file data
- Virtual address base + N refers to offset N in file

Initially, all pages mapped to a file are invalid
- OS reads a page from file when invalid page is accessed
- OS writes a page to file when evicted, or region unmapped
- If page is not dirty (has not been written to), no write needed
	- Another use of the dirty bit in PTE

![[Pasted image 20261111164423.png]]

Advantages
- Uniform access for files and memory (just pointers)
- Less copying

Drawbacks
- Processes has less control over data movement
	- OS handles faults transparently
- Does not generalize to streamed I/O (pipes, sockets, etc.)

