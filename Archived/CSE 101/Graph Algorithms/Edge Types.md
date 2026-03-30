For directed types: (u,v)
Back Edge - an edge leading a vertex to its ancestor
prev(v)<prev(u)<post(u)<post(v)
Forward Edge - an edge leading a vertex to its descendent
prev(u)<prev(v)<post(v)<post(u)
Cross Edge - an edge leading a vertex to neither its ancestor or descendent
prev(v)<post(v)<prev(u)<post(u)
Tree Edge - solid edge included in the DFS output tree
![[Screen Shot 2026-01-12 at 9.47.15 PM.png]]