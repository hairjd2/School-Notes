# Class 6: Programming
## Additional Assembler Info
### Instruction Prefix
- REP: repeats the instruction until cx or ecx = 0 or ZF is set
- LOCK: lock prefix in front of an instruction locks lock peripherals off the system (busses cannot be used during the instruction execution example = out print;)
- ESC: ESC prefix in front of an instruction indicates that the insturction is for 8087; Hex code 11011
## Writing Program Examples
- Program that counts the number of 1's in a byte and writes it into BL
	- ![[Pasted image 20220228174233.png]]
- Program that searches table of 100H bytes for 0AH
	- ![[Pasted image 20220228174421.png]]
- Write a program to move 10 data bytes starting from memory address 25000H to 36000H
	- ![[Pasted image 20220228175522.png]]
### Procedures (functions, calls, subroutines)
- PROC NEAR: 26000H
- PROC FAR: 35000H
## Loading Instructions
### Assembler Loading Instructions
- Load-Effective Address.
	- lea: loads any 32-bit register with the address of the data, as determined by the instruction addressing mode.
	- lds and les: load a 32-bit offset address and then ds or es from a 48-bit memory location
	- lfs, lgs, and lss (80286 and up): load any 32-bit offset address and then fs, gs, or ss from a 48-bit memory location
	- Note: lea calculates the ADDRESS given by the right arg and stories it in the left arg!
- lea vs. mov:
	- ![[Pasted image 20220228180515.png]]
	- 1 and 3 are equivalent
	- 3 is faster than 1 and is preferred
	- However, mov only works with single args and cannot be used with LIST[edi]. lea can take any address, e.g. lea esi, [ebx+edi].
## XLAT
### Translate instruction
- ![[Pasted image 20220228180759.png]]
## DAA 
### Decimal Adjust Accumulator (After Addition)
- ![[Pasted image 20220228180941.png]]
- Adjusts the sum of two packed BCD values to create a packed BCD result. The AL register is the implied source and destination operand. 
- The **DAA** instruction is only useful when it follows an ADD instruction that adds (binary addition) two 2-digit, packed BCD values and stores a byte result in the AL register