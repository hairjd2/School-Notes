# Class 8: Loop Unrolling & Scoreboarding
## ILP
- Processors after 1985 have been using pipelining to overlap instructions
	- This overlapping is known as instruction level parallelism (ILP)
- Pipeline CPI = ideal pipeline CPI + structural stalls + data data hazard stalls + control stalls
	- Decreasing the components on the right hand improves ILP
- In this section we will build on pipelining concepts we have seen previously and how to improve the ILP
- How to improve:
	- Dynamically through hardware at run time
		- Desktops and server processors tend to use the dynamic methods
	- Statically by the compiler at compile time
		- Mobile devices tend to use the static methods
		- However some PMD processors like ARM Cortex A9 are using the dynamic method as well
## Dependences
- Dependences prevent parallel execution of instructions
- There are three different types and they create hazards
### Data Dependences (True Dependency)
- ![[Pasted image 20220619203359.png]]
- Instruction i is data dependent on instruction j if:
	- Instruction j produces a result used by i
	- Instruction i is data dependent on instruction k and instruction k is dependent on j
- There are no dependences within the same instruction
- The order of the instructions must be maintained otherwise they create a hazard
- This limits ILP as data dependent instructions cannot be running in parallel
- To improve ILP we can either:
	- Maintain the dependence and avoid the hazard
	- Get rid of the dependence
### Name Dependence
- Occurs when two instructions use the same register or memory location but there is no data flow between them
- Two types:
	1. Antidependence: instruction j writes to a register/memory location that instruction i reads from
	2. Output depedence: instruction j and i write to the same register/memory location
- In both cases the order must be maintained
- They are not true data dependences
	- Thus can be executed simulatenously
		- or reordered if the name used is changed
- Renmaing can be more easily done with registers than memory
- Can be done statically by the compiler or dynamically by hardware
#### Data Hazards
- Look to Class 5 for definition
- Dependences are a property of the program
- Whether a dependence results results in a hazard being detected is a property of the pipeline organization
#### Control Dependence
- Determines the ordering of an instruction i with respect to a branch instruction
	- Most instructions in the program are control dependent
	- ![[Pasted image 20220622003924.png]]
	- s1 is control dependent on p1, s2 is dependent on p2
- Generally:
	- An instruction control dependent on a branch cannot be moved before the branch
	- An instruction that is not control dependent on a branch cannot be moved after the branch
		- Making it dependent on the branch
- We could violate control dependence if we are able to keep the program correctness
	- Data flow and exception behavior must be maintained
## Basic Pipelining Scheduling
- We will look at a simple technique the compiler uses to exploit ILP
- To keep the pipeline full, parallelism among sequences of unrelated instructions is exploited
- Dependent instructions must be separated from the source by a distance sufficient to alleviate stalls
	- This depends on the amount of ILP available
	- FU's latencies
## Loop Unrolling
- ![[Pasted image 20220622012355.png]]
- Out of the 7 cycles, only 3 work with the array (load, store and add)
	- The other 4 consist of the loop overhead (branch and daddui) and 2 stalls
- Using loop unrolling
	- We can expand out the loop
	- Fill in the stalls
	- and Adjust the loop termination code
- Realize that x doesn't rely on anything out of the loop
	- i is the only shared point
	- If we used different registers, essentially each iteration of the loop would be independent and could be ran in parallel (pipelined)
- ![[Pasted image 20220622012720.png]]
## Scoreboarding
### Static Scheduling
- So far if a dependence cannot be avoided, the compiler inserts a stall and no code is executed until that stall is cleared in order execution
- Static/compiler scheduling
	- Done by the compiler when compiling code
	- One time scheduling cost
	- Compiler might not know what hardware is available so no internal knowledge
- However, what if there are instructiosn that would not have needed the stall
- ![[Pasted image 20220622023856.png]]
### Dynamic Scheduling
- Dynamic Scheduling
	- Done by the hardware
	- Hardware has more information about what is available
		- Changes code according to what is available
	- Easy to port code without recompiling
	- Increased complexity
	- Leads to out of order execution
		- In order issuing
#### Out of Order Execution
- To implement out of order execution we must split the ID stage into
	- Issue: decode instructions and check for structural hazards
	- Read operands: wait until there is no data hazards and read operands
- In a dynamically scheduled pipeline, all instructions pass through the issue stage in order
	- However, they can be stalled or by pass each other in the read stage
- Scoreboarding is a technique used to allow out of order execution as long as there are sufficient resources and no dependencies
## Scoreboarding
- Assuming no structural hazards, the goal is to maintain a 1 instruction per CC rate
	- If current instruction is stalled others can execute as long as they do not depend on any stalled instruction
	- Scoreboard takes responsibility for issue and execution
	- Maintain 1 CPI by executing instructions as early as possible
- Requires:
	- That multiple instructions are in the EX stage
		- Which requires multiple functional units
		- We will assume the system has multiple functional units
	- Knowledge of instructions status
	- Function Unit (FU) status
	- Register result status: which FU will write to which register
- Since integer arithmetic has a shorter latency we will focus mainly on floating point
- Every instruction goes through the scoreboard where
	- A record of the data dependencies is created
		- Replaces part of the ID state
	- Scoreboard determines when instruction can read its operands and begin execution
	- If instruction cannot execute immediately scoreboard monitors hardware and decides when instruction can execute
	- Scoreboard also controls when instruction can write result
- Thus all hazard detection and resolution are handled by scoreboard
### Steps
- ![[Pasted image 20220622200224.png]]
- The new pipeline stages become:
	- Issue
		- Check for structural hazard: is FU busy?
		- Check for WAW: do not issue if an active instruction has the same designation register
	- Read Operands
		- Check for RAW: do not issue is any source register will be written by an active instruction
	- Execution
	- Write Result
		- Check for WAR: stall if necessary
- ![[Pasted image 20220622200213.png]]
- 