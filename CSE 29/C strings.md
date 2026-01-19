C strings are sequences of char (1 byte each) followed by a byte called a null terminator

C strings are often created as arrays
char msg[] = {'H','e','l','l','o','!','$\backslash \emptyset$'};
               72  101 108 108 111   33   0
             And then convert to binary via ascii

