Is it possible to put 8 queens on a chessboard so that no queen is attacking the others?


Brute Force:
- possible answers: $64^8 = 2.8 * 10^14$
Backtracking:
- no queens share a square: $P(64,8)= 1.7*10^14$
- one queen per row: 8^8=16 million
- one queen per column and row: 8! = 40000

Eventual algorithm:
- a possible implementation is to go column  by column, top to bottom, queen down, then eliminate to the right, then go to right column and put queen down. if not possible, then leave, marking that spot as no, and try a different spot in that clumn.