Mealy: Used for smaller really simple circuits.
- Start traversing through the graph, only 1 vertex can be traversed at a time, only one edge can be chosen at a time. Starting on Reset.
- Depending on your input, you should only have one edge available.
- After traversing through that edge, output what it wants to output, and go to the new vertex
Moore: Used for more bigger circuits.
- The output is labeled on the vertex itself, so whenever you receive an input, go down that edge and output the number of whichever vertex you end up in
![[Pasted image 20260216155348.png]]
