# Class 3 (80x86 Architecture)
- ![[Pasted image 20220209174425.png]]
- Example # | Address Bus width | Data Bus Width | Data Bus Width | Memory size | Memory size
 ----- | --------- | -------- | ----------------- | --------- | -------- 
 Example 1 | 
- Example 3:
	- Address bus width bits: 14
	- Data bus width in bytes: 4 bytes
	- Data bus width in bits: 32 bits
	- Memory Size in bytes: 2^14 = 
## Basic Memory Architecture
- 8086 allowed for dual 8 bit bus bank, or a 16 bit bus
- They were separated by odd byte bus and even byte bank
- ![[Pasted image 20220209175616.png]]
- 80386 had the 32 bit bus
### Pentium/Pro/II/III
- Had 8 banks with a total 64 bit bus machine
- Still worked ona 32 bit address range
## Basic IO Architecture
- IO is separate, added stuff to the board
- This can include monitors, keyboards, NIC (Network Interface Card), and the sound card
## Interrupt Vectors (DOS PC)
- Acts whats interrupting the microprocessor what it wants to do
- The address range is inclusive
- The I/O addresses are NOT memory-mapped addresses on the 80x86 machines
## Lab Lec01 Preview 
 ### Structure of an Assembly Language statement: 
- General structure of an assembly language statement
- ```LABEL: INSTRUCTION ;COMMENT```
- Label: address identifier for the statement
- Instruction: the operation to be performed
- Comment: documents the purpose of the statement
- mov: move
- INC: increment
- ADD: add
- ==Labels - Give structure to code and provides target for jump instructions==
- label: instruction operand
	- The ':' is optional, which can cause problems if, for example, you misspell an instruction
	- Valid characters in labels are letters, numbers, '_', $, #, @, ~, ., and ?,
	- Identifier valid starting characters include letters, . , _ and ?
- Local Labels - begin with a '.' and are associated with previous non-local label.
```
label1 ; some code
	.loop ; some more code
	jne .loop ; jump to previous loop
	ret ; treated as label1.loop

Label2 .loop ; some more code
	jne .loop ; jump to previous loop
```
### Assembler and source program
- Assembly program (.asm) file - known as source code
- Converted to machine code by a process called assembling
- Machine (object) code output by assembler needs to be linked and loaded before execution
- Source listing output in (.lst) file - printed and used during execution and debugging of program
### Steps to Running NASM - GDB
1. Produce hello.o object file: 
	- `nasm -f elf hello.asm -l hello.lst`
2.  Produce hello ELF executable (Link and Load)
	- `ld -m elf_i386 -s hello.o -o hello`
3. Run the program
	- `./hello`
### Listing File
- Contents
	- Size of code segment and stack
	- Names, types, and values of constants and variables
	- number lines and symbols used in the program
	- number of errors that occurred during assembly
- `nasm-f elf myfile.asm -l myfile.list`
## 8085 Program: Sequential Processing
- Did a fetch in one clock cycle then executed it in the next cycle
- Need to ==pipeline== the commands, meaning when you execute the first command, you fetch the next command
- **Execution Unit (EU)**: Executes instructions previously fetched
- **Bus Interface Unit (BIU)**: Fetches the instructions, accesses memory and peripherals
 ![[Pasted image 20220209183117.png]]
## Programmer Visible Registers
- The beginning E stands for extended
- EAX(Accumulator)
	- AH means the first 8 bits
	- AL means the least 8 bits
	- AX is the mix of both
- EBX (Base Index)
	- BH
	- BL
	- BX
- ECX (Count)
	- CH
	- CL
	- CX
- EDX (Data)
	- DH
	- DX
	- DL
- ESP (Stack Pointer)
	- SP
- EBP (Base Pointer)
	- BP
- EDI (Destination Index)
	- DI
- DSI (Source INdex)
	- SI
- EIP (Instruction Pointer)
	- IP
- EFLAGS (Flags)
	- FLAGS
- FS -> CS (Code)
- GS -> DS (Data)
- ES (Extra)
- SS (Stack)
