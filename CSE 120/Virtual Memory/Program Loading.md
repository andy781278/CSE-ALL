Loading programs into a process uses mapped files and copy-on-write

Memory Mapped Files
- Executable files is mapped into the address space
- Faults will read from executable file

Copy-on-write
- Code regions mapped read-only (never need to copy)
- Data regions from exe are mapped copy-on-write
	- Only need to make copies if a process modifies a page