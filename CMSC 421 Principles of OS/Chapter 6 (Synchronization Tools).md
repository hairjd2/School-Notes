# Background
- Processes can execute concurrently
	- May be interrupted at any time, partially completing execution
- Concurrent access to shared data may result in data inconsistency
- Maintaining data consistency requires mechanisms to ensure the orderly execution of cooperating processes
- "Suppose that we wanted to provide a solution to the consumer-producer problem that fills **all** the buffers. We can do so by having an integer counter that keeps track of the number of full buffers. Initially, counter is set to 0. It is incremented by the producer after it produces a new buffer and is decremented by the consumer after it consumes a buffer."
- Need some form of mutual exclusion
# The Critical-Section Problem
- Need to actually use a mathematical proof for this
- ![[Pasted image 20221019102544.png]]
## Solution Must Have:
1. **Mutual exclusion** - if process $p_i$ is executing in its critical section, then no other processes can be executing in their critcal sections
2. **Progress** - means that you can't stop all process from entering the critical section
3. **Bounded Waiting** - A bound must exist on the number of times that other processes are allowed to enter their critical sections after a process has made a request to enter its critical section and before that request is granted
# Peterson's Solution
- Not guaranteed to work on modern architectures! (but good algorithmic description of solving the problem)
- Only good for two processes
- Assumes load and store is atomic; that is cannot be interrupted
- Two processes share two variables:
	- `int turn;` - indicates whose turn it is to enter the critical section
	- `boolean flag[2]` - used to indicate if a process is ready to enter the critical section; value of true means ready
# Hardware Support for Synchronization
- Many systems provide hardware support for implementing the critical section code
- Uniprocessors - could disable interrupts
	- Currently running code would execute without preemption
	- Generally too inefficient on multiprocessor systems
- Three forms of hardware support:
## Memory Barriers
- **Memory model** are the memory guarantees a computer architecture makes to application programs
- Memory models may be either:
	- **Strongly ordered** - where a memory modification of one processor is immediately visible to all other processors
	- **Weakly ordererd** - where a memory modification of one processor may not be immediately visible to all other processors
- A **memory barrier** is an instruction that forces any change in memory to be propagated (made visible) to all other processors
## Hardware Instructions
- Special hardware instructions that allow us to either test-and-modify the content of a word, or two *swap* the contents of two words atomically
	- ![[Pasted image 20221019110129.png]]
	- ![[Pasted image 20221019110151.png]]
- Only guarantees bounded-wait if the scheduler guarantees it
## Atomic Variables
- Typically, instructions such as compare-and-swap are used as building blocks for other sync tools
- One tool is an **atomic variable** that provides *atomic* updates on basic data types such as ints and bools
# Mutex Locks
# Semaphores
# Monitors
# Liveness
# Evaluation