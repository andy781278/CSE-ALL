By default, all the virtual address spaces are independent from each other, they are private domains meant to protect access to each other.

Although sometimes we want to share data between processes.

Example: Chrome has a different process for every tab. Those processes all work together as a single application.

Let's use a **Shared Memory** to allow processes to share data using direct memory references
- Both processes can see updates to the shared memory segment

We can use page tables to implement shared memory.
- PTEs in both tables can map to the same physical frame
- Each PTE can have different protection values, so only some can edit and some can read
- Invalid bit applies to all PTEs linked to that physical frame
- Doesn't have to be the same virtual address in different processes

![[Pasted image 20261111163410.png]]

