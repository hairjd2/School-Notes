# Class 5: Pipelining and Hazards
## Pipelining
- According to CAQA: Pipelining is an implementation technique where instructions are overlapped in execution
- Pipelining is a key technique used to make fast CPUs.
### Basic DLX Pipeline
- Specific to MIPS
- Stages
	1. **I**nstruction **F**etch from memory structure
	2. **I**nstruction **D**ecode and operand preparation
	3. **EX**ecute ALU operation and address generation
	4. Data **MEM**ory access
	5. **W**rite**B**ack the result of operations to registers
- ![[Pasted image 20220609191309.png]]
- ![[Pasted image 20220609191447.png]]
## Throughput vs. Latency
- Think of pipeline as an instruction assembly line with each stage progressing at the same time
	- The time it takes to complete one stage is known as the processor cycle
		- Typically 1 clock cycle in a computer
	- For now every step in the pipeline takes a processor cycle
	- Length of the cycle is determined by the slowest stage
- Ideally: $TimePerInstruction=\frac{TimePerInstructionOnUnpipelinedMachine}{NumberOfPipeStages}$
- Throughput is determined by the number of instruction exiting the pipeline in a unit of time
- Latency refers to the number of cycles from one end of the pipeline to another (how long does it take to execute a single instruction)
- Increases throughput at the cost of latency
## Pipeline Breakdown
- ![[Pasted image 20220610204730.png]]
### Instruction Fetch
![[Pasted image 20220610204753.png]]
- Send the PC to memory fetch current instruction. Update Program Counter (PC) by adding 4
- Instruction Memory: Holds instructions
- Add & NPC: Calculates address for the next instruction (pending a branch)
- IR: holds thje instruction once fetched from memory
- NPC <- PC + 4 (Bytes)
### Instruction Decode
![[Pasted image 20220610205120.png]]
- Decode instruction and read the registers
- Registers: Hold a small subset of the total memory for FAST acess
- A & B: These are the operands of the instructions
- Imm: holds and immediate value
### Execution 
![[Pasted image 20220610205815.png]]
- ALU operates on the operands
- Zero and Cond: Test if value is 0 and branch (or don't) based on outcome
- Muxes: Determine input to ALU (branch/jump use NPC, arithmetic use registers)
- ALU: does actual calculation and holds value of result
### Memory Access
![[Pasted image 20220610210047.png]]
- If instruction is a load: memory is read, if it is a store: memory is stored
	- LMD: Load Memory Data holds output from data cache on read
- Mux: can us either NPC from IF or branch target from ALU for PC
### Writeback
![[Pasted image 20220610210024.png]]
- Write back to register if needed
- Mux: determines which values are to be sent back to the register
### Pipeline with Registers
- We need to save state between clock cycles
- Registers are put between stages to hold intermediate data
- ![[Pasted image 20220610212848.png]]
## Hazards
- Hazards are situations that disrupt the normal operation of a pipeline
- Three main categories
	- Structural hazards: resource conflicts when the hardware cannot support all the current instructions
	- Data hazards: instruction depends on a data from a previous instruction that is not yet ready
	- Control hazards: brought about by the pipelining of instructions that affect the PC for example branches
### Structural Hazards
- Assuming we have one memory structure for data and instructions
- When using the same block of memory, accessing it for the MEM and the IF stage can cause a hazard
-  ![[Pasted image 20220610214656.png]]
- Can assume its not a structural hazard unless specified
#### Alleviating Structural Hazards
- Adding a stall (or NOP) can helpp alleviate structural hazards
	- Wait until the resource is available again
	- This wastes cycles
	- ![[Pasted image 20220610215146.png]]
- Duplicate resources
	- Cache can be separated into instruction and data memories
	- ALU can be duplicated to separate branch target and arithmetic instruction needs
- Multiport Memory Cells
	- More than one read and write port to access at the same time
### Data Hazards
- Data hazards occur when the pipeline changes the operand read and write access
- ![[Pasted image 20220610215319.png]]
- ![[Pasted image 20220610220752.png]]
#### Types
- RAW: Read After Write
	1. R1 = ...
	2. ... = R1
- WAW: Write After Write
	1. R1 = ...
	2. R1 = ...
- WAR: Write After Read
	1. 1... = R1
	2. 2R1 = ...
- RAW is the most common
#### Alleviating Data Hazards
- RAW Hazard/Forwarding
	- ![[Pasted image 20220610221212.png]]
	- Can send the data directly to the next execute stage if needed
- Pipeline Interlock - Stalling
	- Is forwarding a total solution for RAW hazards?
		- ![[Pasted image 20220610221621.png]]
		- For load stages, you won't have the data until after the memory stage, which won't give the value in time
	- So you can stall until the memory stage has commenced, then forward the data to the next thing
	- Won't know you need to stall until you reach the ID stage
	- Might need to stall until the data is available
	- ![[Pasted image 20220610221806.png]]
### Control Hazards
- Conditional branches can cause hazards as the outcome of the branch affects the PC
	- We cannot tell the outcome of a branch instruction until after the EX stage
- Branches have two outcomes
	- Pipelines cannot handle both simultaneously so it has to predict the outcome
- To resolve this you could:
	- Move the branch resolution to an earlier stage
	- Stall/freeze the pipeline and wait for the result
		- ![[Pasted image 20220610222607.png]]
	- Predict not taken/taken