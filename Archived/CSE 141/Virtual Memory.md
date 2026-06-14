Similar to caches, virtual memory pulls blocks from disk, turns them into frames that gets stored in main memory (ram), then pull frames from memory and turn them into virtual pages, and then pull cache blocks from pages, and turn them into actual data.

### Virtual Address
Each virtual address carries information for a page (virtual) or a frame (physical)
`[ VPN (36 bits) | Page Offset (12 bits) ]`
`  bits 47-12            bits 11-0        `

48 bits long, each page contains 4KB, which is 2^12, so you can represent it with 12 bits. This means you can find a specific data given the page and the page offset.

Virtual Page Number (VPN) finds the corresponding frame in RAM, if its not found, then the  must be pulled from disk similar to how a cache pulls a cache block from ram. If it is found, then we take the corresponding cache block from that page and puts it in cache.