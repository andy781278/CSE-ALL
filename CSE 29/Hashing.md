Git summarizes your whole commit with a hash, the hash is different when the commit actually changes something. So that's how you'll know if you changed something.

void SHA256(string input, int length, string hash (32 bit)):
- Deterministic: always same output given same input
- One-way: can't decipher the input given the hash output
- Unpredictable: similar inputs have wildly different outputs