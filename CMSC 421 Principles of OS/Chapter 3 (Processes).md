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
- System must provide mechanisms for:
	- Process creation
	- Process termination
### Process Creation
- **Parent** process create children processes, which, in turn create other processes, forming a **tree** of processes
- Generally, processes identified and managed via a **process identifier** (pid)
- Resource sharing options
	- Parent and children share all resources
	- Children share subset of parent's resources
	- Parent and child share no resources
- Execution options
	- Parent and children execute concurrently
	- Parent waits until children terminate
- Address space
	- Child duplicate of parent
	- Child has a program loaded into it
- UNIX examples
	- fork() syscall creates new process
	- exec(), syscall used after a fork() to replace the process' memory space with a new program
	- Parent process calls wait() for the child to terminate
### Process Termination
- Process executes last statement and then asks the OS to delete it using the exit() syscall
	- Returns status data from child to parent (via wait())
	- Process' resources are deallocated by OS
- Parent may terminate the execution of children processes using the abort() syscall. Some reasons for doing so:
	- Child has exceeded allocated resources
	- Task assigned to child is no longer required
	- The parent is exiting and the OS does not allow a child to continue if its parent terminates
- Some OS' do not allow child to exist if parent has terminate.
	- *cascading termination*. All children, grandchildren, etc. are terminated
	- The termination is initiated by the OS
- The parent process may wait for termination of a child process by using the wait() syscall. The call returns status info and the pid of the terminated process: "pid = wait(&status);"
- If no parent waiting (did not invoke wait()) process is a **zombie**
- If parent terminated without invoking wait, process is an **orphan**
- ![[Pasted image 20220926102100.png]]
## Interprocess Communication
- Processes within a system may be *independent* or *cooperating*
- Cooperating process can affect or be affected by other processes including sharing data
- Reasons for cooperating processes:
	- Information sharing
	- Computation speedup
	- Modularity
	- Convenience
- Cooperating processes need **interprocess communication (IPC)**
- Two models of IPC
	- **Shared memory**
		- Disadvantage: have to deal with sharing memory
		- Advantage: memory can be accessed automatically
		- Basically threads "to the extreme" - Lawrence
	- **Message passing**
		- Advantage: can control how process handles the memory
		- Disadvantage: you have to send message everytime you want to share memory
### Producer-Consumer Problem
- Paradigm for cooperating processes, producer process produces information that is consumed by a consumer process
	- **unbounded-buffer** places no practical limit on the size of the buffer
	- **bounder-buffer** assumes that there is a fixed buffer size
## IPC in Shared-Memory Systems
- An area of memory shared among the process that wish to communicate
- The communication is under the control of the users processes not the OS
- Major issues is to provide mechanism that will allow the user processes to synch their actions when they access shared memory
- Synchronization is discussed in detail in Ch. 6 and 7
### Bounded-Buffer - Shared-memory solution
- ![[Pasted image 20220926103342.png]]
#### Producr Process - Shared Memory
- ![[Pasted image 20220926103421.png]]
#### Consumer Process - Shared Memory
- ![[Pasted image 20220926103449.png]]
## IPC in Message-Passing Systems
- Mechanisms for processes to communicate and to synch their actions
- Message system - processes communicate with each other without resorting to shared variables
- IPC facility provides two ops:
	- sends(message)
	- receive(message)
- The message size is either fixed or variable
- If processes P and Q wish to communicate, they need to:
	- Establish a *communication link* between them
	- Exchange messages via send/receive
- Implementation issues:
	- ![[Pasted image 20220926103816.png]]
- Implementation of communication link
	- Physical:
		- Shared memory
		- Hardware bus
		- Network
	- Logical:
		- Direct or indirect
		- Synch or asynch
		- Automatic or explicit buffering
### Direct Communication
- Processes must name each other explicitly:
	- send(P, message) - send a message to process P
	- Receive(Q, message) - receive a message from process Q
	- These two are like the the get_user() and put_user()
- Properties of communication link
	- Links are establish automatically
	- A link is associated with exactly one pair of communicating processes
	- Between each pair there exists exactly one link
	- The link may be unidirectional, but is usually bi-directional
### Indirect Communication
- Messages are directed and received from mailboxes (also referred to as ports)
	- Each mailbox has a unique id
	- Processes can communicate only if they share a mailbox
- Properties of communication link
- Link established only if processes share a common mailbox
- A link may be associated with many processes
- Each pair of processes may share several communication links
- Link may be unidirectional or bi-directional
- Ops
	- create a new mailbox (port)
	- send and receive messages through mailbox
	- destroy a mailbox
- Primitives are defined as:
	- send(A, message) - send a message to mailbox A
	- receive(A, message) - receive a message from mailbox A
- Mailbox sharing
	- $P_1, P_2, P_3$ share mailbox A
	- $P_1$, sends; $P_2$ and $P_3$ receive
	- Who gets the message?
- Solutions
	- Allow a link to be associated with at most two processes
	- Allow only one process at a time to execute a receive operation
	- Allow the system to select arbitrary the receiver. Sender is notified who the receiver was.
### Synchronization
- Message passing may be either blocking or non-blocking
- **Blocking** is considered **synch**
	- *Blocking send* -- the sender is blocked until the message is received
	- *Blocking receive* -- the receiver is blocked until a message is available
- **Non-blocking** is considered asynch
	- *Non-blocking send* -- the sender sends the message and continues immediately
	- *Non-blocking receive* -- the receiver receives a valid message if one is waiting for a NULL message if no valid messages are available immediately
- Different combinations possible
	- If both send and receive are blocking, we have a **rendezvous**
#### Producer - Message Passing
- ![[Pasted image 20220926105641.png]]
#### Consumer - Message Passing
- ![[Pasted image 20220926105706.png]]
### Buffering
- Queue of messages attached to the link
- Implemented in one of three ways
	1. Zero capacity - no messages are queued on a link. Sender must wait for receiver
	2. Bounded capacity - finite length of n messages. Sender must wait if link full
	3. Unbounded capacity - infinite length; Sender never has to wait
## Examples of IPC Systems
### POSIX
- ![[Pasted image 20220926105857.png]]
#### POSIX Producer
- ![[Pasted image 20220926105952.png]]
#### POSIX Consumer
- ![[Pasted image 20220926110020.png]]
### Mach
- ![[Pasted image 20220926110048.png]]
### Windows
- ![[Pasted image 20220926110656.png]]
### Pipes
- Acts as a conduit allowing two processes to communicate
- Issues:
	- either uni or bi-directional
	- For bi-directional: either half or full-duplex
	- Must there exist a relationship between communication processes
	- Can the pipes be used over a network
- *Ordinary pipes* - cannot be accessed from outside the process that created it. Typically, a parent process creates a pipe and uses it to communicate with a child process that it created
- *Named pipes* - can be accessed without a parent-child relationship
#### Ordinary Pipes
- Allow communication in standard producer-consumer style
- Producer writes to one end (the **write-end** of the pipe)
- Consumer reads from the other end (the **read-end** of the pipe)
- Ordinary pipes are therefore unidirectional
- Require parent-child relationship between communicating processes
- Windows calls these **anonymous pipes**
#### Named Pipes
- More powerful than ordinary pipes
- Bidirectional
- No parent-child relationship is necessary between the communicating process
- Several processes can use the named pipe for communication
- Provided on both UNIX and Windows systems
## Communication in Client-Server Systems
### Sockets
- Defined as an endpoint for communication
- Concatenation of IP address and **port** - a number included at start of message packet to differentiate network services on a host
- Communication consists between a pair of sockets
- All ports below 1024 are *well known*, used for standard services
- Special IP address 127.0.0.1 (**loopback**) to refer to system on which process is running