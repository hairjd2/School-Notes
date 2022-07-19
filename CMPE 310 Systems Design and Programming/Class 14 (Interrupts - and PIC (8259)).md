#  Class: Interrupts - and PIC (8259)
## Interrupts:
- The alternative of polling
- Support hardware interrupts through:
	- Two pins that allow interrupt requests, INTR and NMI
	- One pin that acknowledges INTA, the interrupt requested on INTR
- As well as software interrupts
	- INT
	- INTO
	- INT 3
	- BOUND
- Control is provided through
	- IF and TF flag
	- IRET and IRETD
### Interrupt Vector Table
- ![[Pasted image 20220413174416.png]]
### Real and Protected Mode Interrupts
- Order of checking
	1. Other instruction executions
	2. Single-step
	3. NMI
	4. Coprocessor segment overrun
	5. INTR
	6. INT
- If one or more then:
	- FLAGS is pushed onto the stack
	- Both the interrupt (IF) and trap (TF) flags are cleared, which disables the INTR pin and the trap or single-step feature.
	- The CS and IP are pushed onto the stack
	- The interrupt vector contents are fetched and loaded into CS and IP and execution resumes in the ISR.
	- On IRET, CS, IP, and FLAGS are popped
		- IF and TF are set to the state prior to the interrupt.
- The return address (CS/IP) is pushed onto the stack during the interrupt