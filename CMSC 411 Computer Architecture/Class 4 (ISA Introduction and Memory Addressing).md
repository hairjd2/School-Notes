# Class 4: ISA Introduction and Memory Addressing
## Instruction Set Architectures
- A set of operations the compiler will convert code to that corresponds to the hardware
	- An abstract definition of the processor set up, and capabilities
- ISA fills the semantic gap between the user and machine
- The type of processor architecture helps define the instruction set up
- There are four types of architectures:
	1. Stack
	2. Accumulator
	3. Register-memory
	4. Register-register/ load-store
### Stack
- The instruction operands are on the stack
- One operand is taken from the top of the stack while the other is taken from below it.
- The result is stored in place of the second operand
- TOS is updated to point to the result
- Requires specific instructions to access the memory: pop/push
- ![[Pasted image 20220605155403.png]]
### Accumulator
- The accumulator is one of the operands and also the result
- ![[Pasted image 20220605155438.png]]
- ![[Pasted image 20220605155446.png]]
### Register-Memory
- One operand is a register and the other is memory
- The result is stored back in a register
- Can access memory with any instruction
- For add a,b 
	- load r1 a
	- add r2 r1 b
	- store a+b r2
- ![[Pasted image 20220605161444.png]]
### Register-Register or Load-Store
- All operands are registers
- Result is stored to a register
- Requires specific instructions to access the memory: load/store
- ![[Pasted image 20220605161432.png]]
- Most processers after 1980 use this
	- Registers are faster than memory
	- Registers are more efficient
### Example
- ![[Pasted image 20220605161554.png]]
### Architecture Classifictions
#### Classes of Computers
- Computers have different classifications, and these dictate their requirements
	- Personal Mobile Device (PMD)
		- Emphasis on energy efficiency and real time computing
- Desktop computing
	- Emphasis on price-performance
- Servers
	- Availability, scalability, throughput
- Clusters/Warehouse Scale Computers
	- Availability and price perofrmance
	- Software as a Service (SaaS)
- Embedded computers
	- price
#### Classes of Parallelism
- Parallelism is now the driving force for computer design
- Energy and cost are the primary constraints
- Types of parallelism:
	- Data Level Parallelism
		- Operating on different data items at the same time
	- Task Level Parallelism
		- Performing diffferent tasks at the same time
- Hardware exploits these classes of parallelism through:
	- Instruction Level Parallelism
		- Pipelining and speculative execution
	- Vector Architectures and Graphic Processing Units (GPUs)
		- Applies single instruction to a collection of data in parallel
	- Thread Level Parallelism
		- Combines data and task level parallelism
	- Request Parallelism
		- Parallelism among largely decoupled tasks
### Flynn's Taxonomy
- Michael Flynn studied the parallel computing efforts in the 1960s and came us with a simple classification
	- Single Instruction Steam, Single Data Stream (SISD)
		- Uni processor
		- Sequential processor that can still exploit ILP
	- Single Instruction Stream, Multiple Data Streams (SIMD)
		- Same instruction is executed by multiple processors using different data
		- Exploits data level parallelism
		- Vector architecture and GPUs
	- Multiple Instructions Steams, Single Data Stream (MISD)
		- No commercial implementation exists
	- Multiple Instruction Streams, Multiple Data Streams (MIMD)
		- Each processor fetches its own instructions and operates on its own data
		- More flexible than SIMD but also more expensive
### Types of Architecture
- Von Neumann
	- Data and instructions share a common bus
		- Cannont read instructions and data at once
	- The data and instructions memory
	- Typically found in general purpose processors
	- ![[Pasted image 20220605171551.png]]
- Harvard 
	- Data and instructions use separate buses
		- Thus seperate memories for each
	- Higher memory throughput
	- Typically targeted to faster systems
	- ![[Pasted image 20220605171558.png]]
## MIPS (Microprocessor without Interlocked Pipeline Stages) Intro
### Memory Addressing
- Regardless of architecture type, processor must define how memory is addressed.
- Two main issues: Byte ordering and Memory alignment
- Byte ordering
	- Two main types of ordering bytes:
		- Little Endian (Little End)
			- 7 6 5 4 3 2 1 0
		- Big Endian (Big End)
			- 0 1 2 3 4 5 6 7
- Memory alignment
- Access to memory objects larger than a byte must be aligned
- Access is considered aligned if:
	- A mod s = 0. Where A is the address of object and s is the size
- ![[Pasted image 20220606200254.png]]
- Modes: ![[Pasted image 20220606200429.png]]
## RISC VS CISC
- Reduced Ins. Set Computer | Complex Ins. Set Computer
------------ | ------------
Simple, fixed length instructions | Complex, variable length
Few instructions to account for | Many instructions to account for
Only load/store can access memory | Many instructions can access memory
Complex functions need many instructions | Can represent complex functions
Used in most systems | Used in x86 (and a few others)
### Instruction Set Examples:
- ==MIPS== -- main focus
- ARM -- similar to MIPS
- Intel 80x86 -- CISC
## MIPS
- Stands for Microprocessor without Interlocked Pipeline Stages
- ![[Pasted image 20220606211510.png]]
### Example:
- ![[Pasted image 20220606211621.png]]
- ![[Pasted image 20220606212309.png]]
- ![[Pasted image 20220606212335.png]]
- R-type
	- usually directed towards arithmetic operations, 
	- directed to the ALU
	- 32 bits long
- I-type
	- Immediate operations
	- Also 32 bits long
- J-type
	- jumps, traps, returns
	- 22 bits long
## Data Path
- ![[Pasted image 20220606220125.png]]
### R Type Instruction 
- ![[Pasted image 20220606224956.png]]
### I Type Instruction
- ![[Pasted image 20220606225412.png]]
### J Type Instruction
- ![[Pasted image 20220606225505.png]]