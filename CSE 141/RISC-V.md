RISC-V has 6 instruction formats:

### R-type
| funct7 | rs2 | rs1 | funct3 | rd | opcode |
  7 bits   5     5      3       5     7


### I-type
| imm[11:0] | rs1 | funct3 | rd | opcode |
    12 bits    5      3       5     7

### S-type
| imm[11:5] | rs2 | rs1 | funct3 | imm[4:0] | opcode |
     7         5     5      3         5         7

### B-type
| imm[12] | imm[10:5] | rs2 | rs1 | funct3 | imm[4:1] | imm[11] | opcode |
    1          6         5     5      3         4          1         7

### U-type
| imm[31:12] | rd | opcode |
    20 bits     5     7

### J-type
| imm[20] | imm[10:1] | imm[11] | imm[19:12] | rd | opcode |
    1          10         1          8          5     7

