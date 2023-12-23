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
