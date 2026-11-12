For OSes like linux that uses fork() that copies the process to a child process, we need to do a lot of copying data, which takes time.

Instead, for Copy-On-Write philosophy, we try not to copy, and created shared mappings of parent pages in child's virtual address space, so no copying, just give the child the address to the same parent pages, it's just that...

Child processes have the copied pages on read-only, so their protected, so they can't be edited.
- on write, generates protection fault, traps to OS, copy page, change page mapping in client page table, restart write instruciton
- So basically when you do edit it, you make it a new page and redirect the child to that page, separating the shared mapping

![[Pasted image 20261111163957.png]]