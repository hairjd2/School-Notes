# Chapter 3: Processes
## Process Concept
- An OS executes a variety of programs that run as a process
- **Process** - a program in execution; process execution must progress in sequential fashion
- Multiple parts
	- The program code, also called **text section**
	- Current activity include **PC**, processor registers
	- **Stack** containing temp data
		- Function params, return addresses, local variables
	- **Data section** containing global variables
	- **Heap** containing memory dynamically allocated during run time
- Program is *passive* entity stored on disk (**executable file**); process is *active*
	- Program becomes process when executable file loaded into memory
- Executionf of program started via GUI mouse clicks, command line entry of its name, etc.
- One program can be several processes
	- Consider multiple users executing the same program
	- Usually if its read only
- Never want to have the stack run into the heap
### Process State
- As a process executes, it changes **state**
	- *New*: The process is being created
	- *Running*: Instructions being executed
	- *Waiting*: The process is waiting for some event to occur
	- *Ready*: The process is waiting to be assigned to a processor
	- *Terminated*: The process has finished execution
- ![[Pasted image 20220921105629.png]]
### Process Control Block (PCB)
- Information associated with each process (also called **task control block**)
- Process state
- Program counter
- CPU registers
- CPU scheduling information
- Mem-management information - memory allocated to the process
- Accounting information - CPU used, clock timme elapsed since start, time limits
- IO status information - IO devies allocated to process, list of open files
### Threads
- So far, processes have a single thread of execution
- Consider having multiple program counters per process
	- Multiple locations can execute at once (especially on multi-core or multi-CPU systems)
		- Multiple threads of control -> **threads**
- Must then have storage for thread details, multiple PCs in PCB
- Go more into threads in chapter 4
- Want to use list_head instead of linked list
## Process Scheduling
- Max CPU use, quickly switch processes onto CPU core
- **Process scheduler** selects among available processes for next execution on CPU core
- Maintains **scheduling queues** of processes
	- **Ready queue** - set of all processes residing in main memory, ready and waiting to execute
	- **Wait queues** - set of processes waiting for an event (i.e. IO)
	- Processes migrate among the various queues
- ![[Pasted image 20220921110513.png]]
- ![[Pasted image 20220921110537.png]]
### Context Switch
- A *context switch* occurs when the CPU switches from one process to another
- ![[Pasted image 20220921110735.png]]
- When CPU switches to another process, the system must **save the state** of the old process and load the **saved state** for the new process via a **context switch**
- **Context** of a process represented in the PCB
- Context-switching time is overhead; the system does no useful work while switching
	- The more complex the OS and the PCB -> the longer the context switch
- Time dependent on hardware support
	- Some hardware provides multiple sets of registers per CPU -> multiple contexts loaded at once
## Operations on Processes
## Interprocess Communication
## IPC in Shared-Memory Systems
## IPC in Message-Passing Systems
## Examples of IPC Systems
## Communication in Client-Server Systems