# ISA Review
- An ISA includes a specification of the set of opcodes and the native commands implemented by a particular processor
- ![[Pasted image 20220906235639.png]]
## RISC Vs. CISC
- CISC (Complex instruction set computer): VAX, Intel x86, IBM 360/370
- RISC (Reduced instruction set computer): MIPS, ARM, DEC Alpha
- ![[Pasted image 20220906235842.png]]
### RISC Over CISC
- Low complexity
	- Generally results in overall speedup
	- Less error-prone implementation by hardwired logic or simple microcodes
- VLSI implementation advantages
	- Less transistors
	- Extra space for the same area: more registers, cache
- RISC strategy also brings some very important advantages. Because each instruction requires only one clock cycle to execute, the entire program will execute in approx. the same amount of time
- Marketing
### CISC Problems
- Performance tuning unsuccessful
	- Rarely used high-level instructions
	- Sometimes slower than equivalent sequence
- High complexity
	- Pipelining Bottlenecks -> lower clock rates
	- Interrupt handling can complicate even more
- Marketing
	- prolonged design time and frequent microcode erros hurt competitiveness
## Harvard vs. Von Neumann Architecture
- ![[Pasted image 20220907000314.png]]
- ![[Pasted image 20220907000335.png]]
- ![[Pasted image 20220907000345.png]]
# AVR Addressing Modes
- Each instruction has 2 parts:
	1. Opcode: Indicates to ALU what to do
	2. Operands: Numbers on which the ALU operates
## 1. Register Direct (Single Reg)
- Can operate on any of the 32 registers
- Operation:
	- Read contents of register
	- Operate on contents
	- Store back in same register
- Examples: inc, dec, lsl
## 2. Register Direct (Two Reg)
- Two registers:
	1. Rs: source
	2. Rd: dest
- Reads two registers, operates on contents, stores result in dest
- example: add R1, R3: stored in r3
## 3. Immediate Mode
- Constant value is in the instruction
	- Stored in the program code in memory
- Operates on register and immedate, stores value in register
- Example: SUBI R4, 8
## 4. I/O Direct
- Instructions used to access IO space
	- Not extended to IO registers
- IO registers can be accessed using
	- In Rd, PORTADDRESS
	- Out
	- Rd, Rs: any register from register file
	- PORTADDRESS: any register from entire range of 0x00 to 0x3F
### Extended I/O
- For IO registers located in extended IO
	- Commands like "In/Out" cannot be used
	- Use direct and indirect memory instructions
		- LDS and STS combined with SBR, CBR
		- Can also combine with SBRS, SBRC (skip if bit in register if set/clear)
## 5. Data Direct
- Two-word instructions
	- One of the words is the address of the data memory space
	- What is the maximum data memory that can be address in this way?
- Example: STS K, RS // Store Direct SRAM
- Example: LDS Rd, K // K is 16-bit address
## 6. Data Indirect
- Similar to data direct
	- One word each
	- Pointer register (x, y, or z) has base address of data memory
- ![[Pasted image 20220907001312.png]]
- ![[Pasted image 20220907001444.png]]
## 7. Direct Program Addressing
- Call K;
	- Direct subroutine call
	- PC <- k and STACK = PC + 1
## 8. Implicit Adressing
- CLC;
	- Clear Carry C <- o // implicit
- RET; 
	- Subroutine return
	- PC <- STACK
## 9. Indirect Program Addressing
- These instructions use Z register to point to program memory
	- IJMP; // indirect jump to Z
		- PC <- Z
	- ICALL; // Indirect call to (Z)
		- PC <- Z, STACK = PC + 1
## 10. Relative Program Addressing
- Instructions of type RJMP and RCALL
	- Offset of +/- 2k to program counter is used 
- ![[Pasted image 20220907002309.png]]
# Memory Types
- Memory is an array of storage locations
- Address is unsigned binary encoded
- ![[Pasted image 20220907002640.png]]
## Basic Memory Operations
- A inpurts: unsigned address
- d_in and d_out: type depends on application
- Write operation
	- en = 1, wr = 1
	- d_in value stored in location given by address inputs
- Read operation
	- en = 1, wr = 0
	- d_out driven with value of location given by address inputs
- Idle: en = 0
## Memory types
- ![[Pasted image 20220907002946.png]]
- ![[Pasted image 20220907003027.png]]
- ![[Pasted image 20220907003015.png]]