# Class 7: Multicycle Pipelines
## Multicycle Operations
- Not all instructions can complete in one cycle
	- Multiplication/division typically take multiple cycles
	- Floating point operations also take multiple cycles
		- Otherwise we would have to accept a slow clock
- For this section we will assume the ALU is made of 4 major components:
	- Main integer unit for loads, stores, integer arithmetic/logical operations, branches
	- FP and integer multiplier
	- FP arithmetic/logic 
	- FP and integer divider
- The EX stage can be repeated as many times as needed
- We will stall if there is potential for a data or structural hazard
- ![[Pasted image 20220618120726.png]]
## Long Latency Operations
- Assuming that the EX stage is not pipelined
	- We need to define latency and initiation intervals to allow for pipelining
		- Latency is time until the result can be used (from the start of the EX stage)
		- Initiation interval: time that must pass before issuing operations of the same type
- Divide is not typically pipelined
- ![[Pasted image 20220618121219.png]]
	- Indicates how many cycles after first execute
## Multicycle Hazards
- Division is not pipelined creating structural hazards
- Number of register writes per cycle could be greater than 1
- WAW hazards are possible since WB is out of order
- Instructions complete out of order creating issues for exception handling
- RAW hazards are more frequent
![[Pasted image 20220619215246.png]]
