https://www.youtube.com/watch?v=d4Pgi5XML8E
# Process of Code
1. Preprocessing passes over the source code, performing
	- Comment removal
	- Macro expansion
	- include expansion
	- conditional compilation (IFDEF)
2. Compiling takes C code and puts it into assembly
3. Assembler converts assembly code into binary opcodes
	- Each instruction is represented by a binary opcode
	- The assembler will produce an object file
		- Object files contain machine code
		- This file will contain fields to be filled by the linker
4. Linking is used to define memory regions on embedded platforms
	- More is needed before the object code can be executed
	- The result of linking is the final executable program
# Output Formats
- The output of the compilation process can take many forms
	- PE
	- ELF
	- Mach-O
	- COFF/ECOFF
- This output file is often your starting point as a reverse engineer
## ELF Files
- ELF = Executable Linking Format
- Contains information identifying:
	- OS, endianness, etc.
- ELF files provide information needed for execution by the OS
- ELF Files can be broken up into three components
	- ELF header
	- Sections
	- Segments
- Symbols are used to aid in debugging and provide context to the loader
	- Removing these symbols makes RE harder
- ELF objects contain a maximum of two symbol tables
	- .symtab: Symbols used for debugging/labelling (useful for RE)
	- .dynsym: contains symbols needed for dynamic linking
	- 