### Format Specifiers
printf("%c",var) -> prints var formatted as ASCII character
printf("%d",var) -> prints var formatted as decimal number

`%hh other` - interpreted as unsigned char
`%c` — single character (uses the ASCII/byte value)  
`%d` or `%i` — signed decimal integer  
`%u` — unsigned decimal integer
`%o` — unsigned octal  
`%x` / `%X` — unsigned hexadecimal (lowercase / uppercase)

`%f` — floating-point in decimal form (default is 6 digits after the decimal)  
`%lf` — technically the same in `printf` (the `l` matters for `scanf`, not here)  
`%e` / `%E` — scientific notation  
`%g` / `%G` — “smart” float: chooses `%f` or `%e` based on size

`%s` — null-terminated C string (`char *`)  
`%p` — pointer address (implementation-defined format, usually hex)

Length modifiers change how the argument is interpreted:

`%hd` — `short`  
`%ld` — `long`  
`%lld` — `long long`  
`%zu` — `size_t` (this one matters on 64-bit systems)

You can also control formatting:

`%6d` — minimum width  
`%.2f` — precision (2 digits after decimal)  
`%06d` — zero-padded  
`%-6d` — left-aligned


Possible Errors:
- Mismatched # of format specifiers and values
- no way to format a value with given specifier
- 