# Buffer Overflows
- When a buffer has data written to it that exceeds the size of the buffer, a buffer overflow occurs
	- The excess data continues to write, overflowing into nearby variables and other areas of memory
- ![[Pasted image 20230708001934.png]]
## Stack Allocation
- Memory located by the program as it runs
- e.g.
	- Local variables
	- Function calls
- Somewhat fixed at compile time
## Heap Allocation
- Dynamically allocated memory
## Overflowing the Stack
- Requires the use of a lower-level langue that will allow the use of unsafe functions and methods
- End goal is to use the overflow to overwrite important things
	- Return addresses
	- Function params
	- "Normal" memory with code supplied by the attacker
## Seg Faults
- Happens when memory is written to that should not be
- Or when memory that is accessed should not be
- Not 100% consistent
# Vulnerable Code
## Finding Vulnerable Code
- Easisest way is to inspect source code
- Trace execution of programs
- Brute force or "fuzz" a program with large inputs to see if errors arise
## Avoiding Vulnerable Code
- Ensure that buffers only take in the amount of data they can actually hold
- Enforce size limits on inputs
- Use a higher-level language when needed
- Don't use bad, outdated functions
- ![[Pasted image 20230708002515.png]]
- ![[Pasted image 20230708002530.png]]
# Exploiting Stack Overflows
## Overwriting Return Addresses
- Want to control where the program "returns" to after a function is completed
- If we can force it to return to somewhere in memory where malicious code, then it will execute that code instead
- Accomplish this by overwriting the actual return address with one of our own making
## Shellcode
- Malicious code that we want to run
- ![[Pasted image 20230708002726.png]]
## NOP Sleds
- ![[Pasted image 20230708002740.png]]
# Daily Security Tidbit
- ![[Pasted image 20230708002801.png]]