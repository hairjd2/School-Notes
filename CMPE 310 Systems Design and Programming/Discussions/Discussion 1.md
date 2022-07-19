# Discussion 1: Intro to NASM
- mov ax, bx means it moves the value of bx into ax
- The heap stores dynamically allocated memory
- The stack stores function parameters
- 0xA defines a new line
## NASM Labels
- **Labels** - Give structure to code and provides target for jump instruction
- **label: instruction operand
	- The ':' is optional, which can cause problems if, for example, you misspell an instruction
	- Valid characters in labels are letters, numbers, _, $, #, @, ~, ., and ?.
	- Identifier valid starting characters include letters, ., _, and ?.
- **Local Labels** - begin with a '.' and are associated with previous non-local label. 
- jne represents the ability to jump
- When you say ```jne .loop``` you are jumping from the loop