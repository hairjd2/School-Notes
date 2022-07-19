# Class 3: Performance and Benchmarks
## Performance Introduction
- Computer technology has made a lot of progress since the first general purpose computer.
	- Less than $500 can get you more computing power than what sent the man to the moon
- Intro to microprocessor increased the rate of growth
- The elimination assembly language programming and standardization of vender independent OSs increased growth of new architecture
	- This led to dev of RISC architecture (Reduced Instruction Set Computer)
### Trends
- Intro of RISC architecture coupled with developments in hardware further increased technology growth
- Around 2003, this growth dropped:
	- Maximum power dissipation of air cooled chips
	- You can only leverage instruction level parallelism for so long
- Solution:
	- The microprocessor
	- ![[Pasted image 20220603003906.png]]
	- 
- Moore stated that the number of transistors that could fit on a chip would double every year. 
	- Later amended to two years in 1975
	- Doesn't hold true anymore
## Power and Energy
- Power is one of the biggest issues facing designers today
	- Getting power in, dealing with power going out
- Thermal Design Power (TDP) is the maximum theoretical load
	- Characterizes sustained power consumption
	- Used to design power supply and cooling systems
- Clock rate can be reduced dynamically to limit power consumption
- Energy per task is usually a better measurement when we have fixed workload
	- Power is energy over time so does not account for actual task
- For CMOS chips, the primary energy consumption is in transistor switching.
	- Also known as Dynamic Energy
	- For one pulse (1-0-1 or 0-1-0)
		- $E=CV^2$
	- Thus for one change 0-1 or 1-0
		- $E=\frac{1}{2}C*V^2$
		- **We will use this for calculations in this class**
	- Dynamic Power:
		- $P=\frac{1}{2}CV^2f_{switched}$
### Increase in Clockrate
- ![[Pasted image 20220603213445.png]]
### Increasing Energy Efficiency
- Do nothing well:
	- Turn off the clock for inactive modules
- Dynamic Voltage Frequency Scaling (DVFS)
	- Operate devices at lower frequencies and voltages during times of low activity
- Design for typical case
- Overclocking:
	- Turbo mode in intel chips
### Static Power
- Static Power = Static Current x Voltage
- Leakage current still flows when the transistors are idle
- Thus the more transistors, the more leakage current, the more static power dissipated
- As more transistors are put on chips, static power is becoming an issue
- The more and more dissipation of power can cause overheating even if it is not doing anything
- How to fix this issue?:
	- Completely turn off the power to the system to stop any current from flowing 
## Performance cont.
### Performance
- Bandwidth/throughput:
	- Total work done in a unit of time
- Latency/response time
	- Time between start and completion of an event
- Examples:
	- Replacing the processor of a computer with a faster version
		- Enhances BOTH response time and performance
	- Adding additional processors to a system that uses multiples processors for separate tasks (e.g. handling of airline reservations system)
		- Improves ONLY throughput
- Computer performance is typically measured using:
	- Response time
	- Throughput
- Maximizing performance means minimizing response (execution) time
	- $Performance=\frac{1}{ExecutionTime}$
- When we say one computer is faster than another we typically mean:
	- $\frac{X_{ExecutionTime}}{Y_{ExecutionTime}}=\frac{Y_{Performance}}{X_{Performance}}$
- How to measure execution time:
	- Wall clock time
		- Time it takes to complete a task system wide
			- Includes OS over head, memory access, I/O requests and so on
		- But with multiprogramming this might not be as accurate
	- CPU time
		- Time the processor spends on a task excluding I/O requests or time spent on other tasks
### Machine Clock Rate

- ![[Pasted image 20220603215304.png]]
### CPU Time
- CPU time expression:
	- CPU cycles for a program x Clock cycle time
	- CPU cycles for program / Clock rate
- Another important metric is how many cycles each instruction takes, Cycles Per Instruction (CPI)
	- CPI = CPU cycles for a program / instruction count (IC)
	- CPU cycles = CPI x IC
- $CPU Time = \frac{Instructions}{Program}*\frac{Clock Cycle}{Instruction}*\frac{Seconds}{Clock Cycle}=\frac{Seconds}{Program}$
## Improving performance
- From the pervious formula we see processor performance depends on:
	- Clock cycle (rate)
	- Cycles per instruction
	- Instruction count
- Improving one will improve performance
	- Unfortunately, this will also influence the others
	- Usually this effect is small or measurable
- Clock cycle is usually published by the manufacturer
- However, measuring CPI and IC is not trivial
- Recall: Performance = 1/Execution time
- To improve performance you can reduce execution time
	- Exploiting parallelism
	- Exploit locality
	- Focus on the common case
- IC can be measured by:
	- Software profiling
	- Using an architecture simulator
- CPI depends on many factors including:
	- Processor structure
	- Memory system
	- Instruction types and implementation
- CPU cycles = CPI x IC or $CPU Clock Cycles=\sum_{i=1}^{n}CPI_iC_i$
	-  Where $C_i$ is the number of instructions of class i that gets executed
	- $CPI_i$ is the avg number of cycles per instruction for that instruction class
	- n is the number of different instruction classes
### Comparing Code Segments
- Compiler designer is trying to decide between two code sequences for a particular machine. The hardware designers have supplied the following facts:
	- ![[Pasted image 20220604111509.png]]
- For a particular high-level language statement, the compiler writer is considering two code sequences that require the following ICs:
	- ![[Pasted image 20220604113824.png]]
- Questions
	- Which code sequence executes the most instructions:
		- Sequence 1: 2 + 1 + 2 = 5 instructions
		- ==Sequence 2: 4 + 1 + 1 = 6 instructions==
	- Which one is faster:
		- Sequnce 1: cycles = (2x1) + (1x2) + (2x3) = 10 cycles
		- ==Sequnce 2: cycles = (4x1) + (1x2) + (1x3) = 9 cycles==: Sequence 2 is faster
	- What is the CPI for each sequence:
		- CPI = Cycles / IC
		- Sequence 1: CPI = 10/5 = 2
		- ==Sequence 2: CPI = 9/6 = 1.5==
### Determinants of CPU Performance
- CPU Time = IC x CPI x Clock_Cycle
- ![[Pasted image 20220604115036.png]]
- Example:
	- ![[Pasted image 20220604141111.png]]
	- Questions
		- How much faster would the machine be if a better data cache reduced the average load time to 2 cycles?
			- ![[Pasted image 20220604141248.png]]
			- CPU time new = 1.6 x IC x CC sp 2.2/1.6 means 37.5% faster
		- How does this compare with using branch prediction to shave a cycle off the branch time?
			- ![[Pasted image 20220604141317.png]]
			- CPU time new = 2.0 x IC x CC so 2.2/2.0 means 10% faster
		- What if two ALU instructions could be executed at once?
			- ![[Pasted image 20220604141448.png]]
			- CPU time new = 1.95 x IC x CC so 2.2/1.95 means 12.8% faster
## Amadahl's Law
- The performance improvement that can be gained from using an improvement is limited by the fraction of time that improvement can be used
- Or simply:
	- Speed up = old execution time (without enhancement) / new execution time
	- $ExecutionTime_{new}=ExecutionTime_{old}*((1-Fraction_{enhanced})+\frac{Fraction_{enhanced}}{Speedup_{enhanced}})$
	- or $Speedup=\frac{1}{((1-Fraction_{enhanced})+\frac{Fraction_{enhanced}}{Speedup_{enhanced}})}$
### Example:
- ![[Pasted image 20220604154820.png]]
## Benchmarks
- Benchmarks are programs used to measure a computer's performance
- Benchmarks used in the past include:
	- Snythetic progreams made to mimic real world applications
	- Toy programs like quick sort
	- Kernels: small key pieces of real applications
	- These have been discredited today
- Typically the best choice of benchmarks are real world applications
- Benchmark suite is typically used during benchmarking
	- A collection of applications
- Some common benchmark suites include:
	- EEMBC (Embassy)
	- SPEC
	- Coremark
### Reporting Performance
- ![[Pasted image 20220604171939.png]]
- Wrong summary can present a confusing picture
	- A is 10 times faster than B for program 1
	- B is 10 times faster than A for program 2
- Total execution time is a consistent summary measure
	- $\frac{Performance_B}{Performance_A}=\frac{ExecutionTime_A}{ExectionTime_B}=\frac{1001}{110}=9.1$
- Assuming that programs 1 and 2 are executing for the same number of times on computers A and B
- Could use the Arithmetic Mean for execution time
	- Still does not fully account for the differences in times programs execute
- To account for this we could use weighted arithmetic means
	- Summarizes performance while tracking frequency as well
- Alternatively we can use weights that normalize performance to a reference machine
	- Can bias performance to that machine
- We could use ratios of execution time to reference machine
	- Less chance of bias to reference machine
- ![[Pasted image 20220604181013.png]]
- We can use Geometric mean to get performance summary
- $GM=\sqrt[n]{\prod_{i=1}^{n}ExecutionTimeRatio}$
- Geometric mean is more suitable than arithmetic mean for normalized execution
- When reporting results, they should be reproducible
	- List everything needed reproduce your results
## Million Instructions Per Second (MIPS)
- A simple and intuitive performance metric
	- Faster machines have bigger MIPS
- $MIPS=\frac{IC}{ExecutionTimex10^6}$
- Is valid in a limited context
- There are three problems with MIPS:
	- MIPS specifies the instruction execution rate but does not take into account the capabilities of the instructions
	- Computers do not have the same MIPS rating, as MIPS varies between programs on the same computer
	- MIPS can vary inversely with performance
### Example
- Consider the machine with the following three instruction classes and CPI:
	- ![[Pasted image 20220604182347.png]]
- Now suppose we measure the code for the same program from two different compilers and obtain the following data:
	- ![[Pasted image 20220604182423.png]]
- Assume that the machine's clock is 500MHz. Which code sequence will execute faster according to MIPS? According to Execution time?
	- ![[Pasted image 20220604182508.png]]
	- ![[Pasted image 20220604183614.png]]