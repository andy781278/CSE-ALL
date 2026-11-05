put your keys in a .env file and put that in .gitignore so it's not in your source code

Anything that charges money to use should have a key, and that key can be used by anyone to use it and charge you.

Don't keep passwords as plaintext, store cryptographic hashes, it's un-invertable, unless if you have quantum computers ig

Cracking:
### Brute force
try everything
have large space of passwords with non-common words to mitigate
### Rainbow table
precomputed hashes of common passwords
use salts to mitigate

Each user gets a random salt that alters the hash, so two users with same password gets different hashes, also makes it harder to brute force, nearly impossible