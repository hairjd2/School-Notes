# Class 5: Addressing Modes and Instruction Set
## Addressing Modes
### Numbers
- #### Register and Immediate data
	1. Register Addressing
		- mov AL, CL - 8 bit transfer
		- mov AH, CL - Mix upper and lower bytes
		- mov AX, CX - 16 bit transfer
		- mov EAX,ECX - 32 bit transfer
	2. Immediate Addressing
		1. 
- #### Memory Data
	3. Direct Addressing
	4. Register Indirect Addressing
	5. Based Addressing
	6. Indexed Addresing
	7. Based Indexed Addressing
	8. String Addressing
		- Employed in string operations to operate on string data
		- The Effective Address (EA) of source data is stored in SI register and the EA of destination is stored in DI register.
		- Segment register for calculating base address of source data is DS and that of the destination data is ES
- #### I/O Ports
	9. Direct I/O port Addressing
		- These addressing modes are used to access data from standard I/O mapped devices or ports.
		- In direct port addressing mode, an 8-bit port address is directly specified in the instruction.
		- Example: IN AL,[09h] - Content of port with address 09h is moved to AL register
	10. Indirect I/O port Addressing
		- In indirect port addressing mode, a 16-bit port address is specified in a register.
		- Example: in AL,[DX] - Content of port with address in register DX is moved to AL register.
		- Can be a byte or word transfer in 8086
		- In 32-bit systems, can be bytem word 
- #### Other
	11. Relative Addressing
	12. Implied Addressing
### Segments
- The number of address lines in the 8086 is 20
- To allow access to one of the 1MB memory locations.
- The Internal has four segment registers to work with only 16 bit wide size
- Each segment can address 64 KB
- Each segment is made up of contiguous memory locations
- It is an independent, separately addressable unit
- Starting address will always be changing, it will not be fixed.
## Instruction Format
- Different for all processors
- Format for 8086:
- ### Byte 1
	- Opcode (Operation (Instruction) Code)
	- D (Direction is to register/direction is from register)
	- W (Word/Byte operation)
- ### Byte 2
	- MOD (Register Mode/Memory Mode with Displacement length)
	- REG (Register Operand/Extension of Opcode)
	- R/M (Register Operand/Registers to use in EA calculation
- ### Byte 3: LOW DISP/DATA
- ### Byte 4: HIGH DISP/DATA
- ### Byte 5: LOW DATA
- ### Byte 6: HIGH DATA
## Instruction Set - Data Xfer
1. Data Transfer Instructions
	- Instructions that are used to transfer data/address in to registers, memory locations and I/O ports
	- Generally involve two operands: Source operand and Destination operand of the same size
	- Can push and pop onto the stack
	- The stack is LIFO
	- Mnemonics: mov, xchg, push, pop, in, out
2. Arithmetic Instructions
	- ADD: adds two numbers together
	- ADC: add with carry
	- SUB: subtract with two numbers
	- SSB: Subtract with borrow
	- INC and DEC: increment and decrement
	- MUL: multiply (unsigned)
	- DIV: divide (unsigned)
	- IDIV: integer divide (signed)
	- CMP: compare
3. Logical Instructions
	- XOR: exclusive OR; can invert second if first is 1, won't invert the second if the first 0
	- TEST: and function to flags, no result
	- SHR: shift logical right
	- SHL: shift logical left
	- RCR: rotate thru carry flag, right
	- RCL: rotate thru carry flag, left
4. String manipulation Instructions
	- MOVS: move byte/word (string...)
	- CMPS: compare byte/word (string...)
	- REP: repeat (string operation...)
	- SCAS: scan byte/word (string...)
	- LODS: load byte/word to AL/AX
	- STOS: store byte/word from AL/A
5. Process Control Instructions
	- STD: set direction flag
	- CLD: clear direction flag
	- STC: set carry flag
	- CLC: clear carry flag
	- CMC: compliment carry flag
	- STI: set interrupt flag
	- CLI: clear interrupt flag
	- NOP: no operation
	- HLT: halt(after interrupt set)
	- WAIT: wait for test pin
	- ESC: escape to external device
	- LOCK: bus lock prefix
6. Control Transfer Instructions
	- CALL: Used to call a subroutine
		- Works in coordination with the RET instruction
		- To calculate the address, the offset specified by the label L1 is added or subtracted from the current address of the JMP instruction
		- If its a forward jump, then the offset is added. EIP will hold this value
		- Opposite for a backward jump.
	- RET: return from subroutine
	- JMP: unconditional or conditional jump
		- Simply updates EIP to the location specified by its one and only operand.
		- To calculate the address, the offset specified by the label L1 is added or subtracted from the current address of the JMP
		- Forward and backwards jumps work similar to the CALL command
		- Operands:
			- JNC: jump not carry
			- JE, JNE, JZ, JZ: jump equal/zero, not equal/zero
			- JA, JB, JAE, JBE: jump above/below/or equal
			- JG, JL, JGE, JLE: jump greater/less/equal to
			- JO, JNO: jump overflow/not overflow
			- JS, JNS: jump sign/no sign
			- JPO, JPE: jump parity odd/even
			- JCXZ: jump if CX == 0