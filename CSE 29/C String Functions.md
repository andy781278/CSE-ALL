int **strlen**(char* str) - gives the number of bytes (not including null terminator)

void **strcpy**(char* dest, char* src) - copies src to dest

void **strcat**(char* dest, char* src) - appends src to end of dest

char* **strtok**(char* str, char delimiter) - parses str between delimiters, only returns the first parsed segment, then the second when you call NULL with the same delimiter, or don't, and it uses the new delimiter.

int **strcmp**(char* s1,char* s2) - compares two strings lexicographically. Return 0 if they are equal, <0 if first char that does not match is lower in s1 than in s2. >0 for first char bigger in s1 than s2.

char* **strstr**(char* haystack, char* needle) - finds the needle in the haystack, finds the first substring needle in haystack and returns the first character of the substring if found, NULL if not found, haystack if empty needle.