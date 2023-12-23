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
0: NOP → no operation
1: LDA addr/imm16 → A = addr/imm16
2: STA addr/imm16 → addr/imm16 = A
3: ADD addr/imm16 → A = A + addr/imm16
4: SUB addr/imm16 → A = A - addr/imm16
5: LPC → A = PC
6: JMP not_zero/overflow → PC = imm16
7: OUT halt/no_halt → O = A & halt/no_halt
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

