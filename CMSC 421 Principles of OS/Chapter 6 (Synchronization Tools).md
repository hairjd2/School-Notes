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
- Previous solutions are complicated and generally inaccessible to application programmers
- OS designers build software tools to (at least partially) solve the critical section problem
- Simplest is mutex lock
- Protect a critical section by first `acquire()` a lock then `release()` the lock
	- Bool indicating the lock is available or not
- Calls to `acquire()` and `release()` must be atomic
- Can be implemented with **busy waiting**
	- Also called **spinlock**
- Often implemented with a **wait queue** to avoid busy waiting
# Semaphores
- Synch tool primitive that gives you more sophisticated ways to for process to synch their activities
- Semaphore S - int var
- Can only be accessed via two indivisible (atomic) ops
	- `wait()` and `signal()`
		- Originally `P()` and `V()`
- **Counting semaphore** - int value can range over an unrestricted domain
- **Binary semaphore** - int value can range only between 0 and 1
	- Essentially the same as a **mutex lock**
- Can solve various synch problems
- Consider $P_1$ and $P_2$ that require $S_1$ to happen before $S_2$ 
- Can implement a counting semaphore S using a binary semaphore
# Monitors
- High-level abstraction that provides a convenient and effective mechanism for process synching
- Abstract data type, internal variables only accessible by code within the procedure
- Only one process may be active within the monitor at a time
## Condition Variables
- `Condition x, y;`
- Two ops are allowed on a condition variable:
	- `x.wait()` - a process that invokes the op is suspended until `x.signal()`
	- `x.signal()` - resumes one of processes (if any) that invoked `x.wait()`
		- If no `x.wait()` on the variable, then it has no effect on the variable
# Liveness
- Processes may have to wait indefinitely while trying to acquire a synch tool
- Waiting indefinitely violates the progress and bounded-waiting criteria discussed at the beginning of this chapter
- **Liveness** refers to a set of properties that a system must satisfy to ensure processes make progress
- Indefinite waiting is an example of a liveness failure
- **Deadlock** - two or more processes are waiting indefinitely for an event that can be caused by only one of the waiting processes
- **Starvation** - indefinite blocking
- **Priority Inversion** - Scheduling problem when lower-priority process holds a lock needed by higher-priority process
	- Solved via **priority-inheritance protocol**
## Priority Inheritance Protocol
- ![[Pasted image 20221024111215.png]]
# Evaluation