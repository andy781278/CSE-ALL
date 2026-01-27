C strings are sequences of char (1 byte each) followed by a byte called a null terminator

C strings are often created as arrays
char msg[] = {'H','e','l','l','o','!','$\backslash \emptyset$'};
               72  101 108 108 111   33   0
             And then convert to binary via ascii

When you pass an array, you pass the pointer of its first element, so you pretty much pass it by reference
- When you need to alter an array, instead of altering it, you put the changed elements into another array, so that pretty much half deep copies it and half alters it in the same function

char* s = char s[]
These mean the same thing, since an array variable only stores the address of the first element.

int strlen(char* str) - gives the number of bytes (not including null terminator)
void strcpy(char* dest, char* src) - copies src to dest
void strcat(char* dest, char* src) - appends src to end of dest

