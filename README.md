# DIRT-16
The DIRT-16 is a 16-bit fantasy computer for recreational computing and retro-inspired game development. Features are described below.

## Project Goals
- 16-bit CPU
- Runs on binaries (Will provide assembler and language with compiler)
- Capable of graphics and sound (3d if possible)
- Frontend that emulates screen and data drive interface
- More powerful than the SNES but less than the N64
- Circuit-switched networking a-la dial-up

## Todo list
- [ ] Implement Backend (CPU emulation library and related things)
- [ ] Implement Frontend (Computer with screen reading from framebuffer and drive port to place ports in)
- [ ] Create assets for frontend
- [ ] Clearer documentation of technical aspects

## System Specification
- 24MHz master clock, 6MHz CPU clock (i.e. 4 master clock cycles per CPU cycle)
- 16-bit word size, 32-bit addr size
- 512kb memory, 512kb data drive
- 640x480 framebuffer

## CPU Specification
- 6MHz
- 6 registers (r0, r1, r2, r3, r4, r5)
- Program Counter
- Stack Pointer
- Status Register, 8-bit (INVZC)
    - IRQ disable (I)
    - Negative (N)
    - Overflow (V)
    - Zero (Z)
    - Carry (C)
    - 3 status bits reserved for user
        - X, Y, W
- Interrupts
    - IRQ
    - NMI (non-maskable)
    - RESET
    - ABORT
- Vectors at end of ROM a-la 6502
- Conditional execution a-la ARM (b, beq as branch and branch if equal)
- Opcode structure
    - 0000000000000000
    - ---- instruction
    -     ---- addressing mode
    -         --------
- Argument types
    - Rx
    - $ADDR
    - $(ADDR+Rx)
    - #HEXNUM
    - d#DECNUM
    - b#BINNUM
- ASM Instructions
    - LDR Rx ADDR
    - STR Rx ADDR
    - ADD Rx Ry Rz
    - SUB, same args as ADD
    - MUL, same args as ADD
    - DIV, same args as ADD
    - POP {Rx, PC, SR, SP}
    - PSH {Rx, PC, SR, SP}
    - NOP
    - BRA $ADDR
    - CLx
        - CLI, CLN, CLV, CLZ, CLC, CLX, CLY, CLW
    - SEx
        - SEI, SEN, SEV, SEZ, SEC, SEX, SEY, SEW
    - INC Rx
    - DEC Rx
    - STP
    - SWP Rx Ry
    - 
    - 
