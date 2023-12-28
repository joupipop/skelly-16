# skelly-16
A 16-bit computer emulator with custom architecture and instruction set.
## Architecture
### Registers
```
A: GP register
B: operation register (stores the second term in an operation)
F: ALU flags (zero, overflow)
O: output register
PC: program counter
```
### Instruction set
```
0: LDA addr/imm12 → A = addr/imm12
1: STA addr/imm12 → addr/imm12 = A
2: ADD addr/imm12 → A = A + addr/imm12
3: SUB addr/imm12 → A = A - addr/imm12
4: LPC → A = PC
5: JNZ imm12/L+imm8 → PC = imm12/L+imm8
6: OUT halt/no_halt → O = A & halt/no_halt
7: LDI imm8 → L = imm8 | ldi $imm8
```
See the [spec](specs.txt) for more information.

## Assembly
Assembly programs can be [assembled](assembly) to machine code which can be run by the emulator.<br>
Assembly has 7 different base instructions, new ones can be added with the use of macros; a single instruction that is expanded to several base instructions.<br>
The 7 base instructions correspond directly to the 7 instructions in the instruction set.<br>
### Example assembly program (computes the Fibonacci sequence)
```
0: $0
1: $1
2: $0
3: lda 0
4: add 1
5: sta 2
6: lda 1
7: sta 0
8: lda 2
9: sta 1
a: out
b: jmp nz 3
```

## Skelangton
Skelangton is a high level programming language that can be [compiled](skelangton) to assembly code.
### Example skelangton program (whole part division of 16 and 3)
```swift
func div(x, y)
{
  i = 0;
  while (x >= y)
  {
    x = x - y;
    i = i + 1;
  }
  return i;
}

division = func(16, 3);
out(division);
```

