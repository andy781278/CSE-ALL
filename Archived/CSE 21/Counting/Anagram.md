#Counting
if you have n characters, you have n! anagrams, unless a letter repeats

This technique is known as the [[Quotient Rule]]

Case repeating letters:
1. first, treat the repeating letters as unique letters, that makes n! anagrams give n characters
2. Then, for every repeating group, divide the answer by the number of repeating letters

TE1E2S and TE2E1S, this counts every anagram twice
So you should divide by 2! to get the final answer

for OOFFN, divide by 2! * 2!