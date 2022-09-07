# Chapter 1 (Introduction)
- Overview chapter
# Computer system
- Divided into four components:
	1. Hardware
	2. OS
	3. Application programs
	4. Users
		1. People, machines, other computers
- OS is  a resource allocator and control program making efficient use of HW and managing execution of user programs
- Users of dedicate systems such as workstations have dedicated resources but frequently use shared resources from servers
- Mobile devices like smartphones and tables are resource poor, optimized for usability and battery life
	- Mobile user interfaces such as touch screens, voice recognition
- Some computers have little or no user interface, such as embedded computer
- One program that is always running is the kernel, part of the OS
- Everything eles is either:
	- A System program (ships with the OS, but not part of the kernel)
	- Or an application program, all programs not associated with the operating system
- OSes include middleware, which are a set of software frameworks that provide additional services
## Operation
- IO devices and the CPU can execute concurrently
- Each device controller is in charge of a particular device type
- Each device controller has a local buffer
- each controller type has an OS device driver to manage it
- CPU moves data from/to main memory to/from local buffers
- IO is from the device to local buffer of controller
- Device controller infroms CPU that it has finished its operation by causing an interrupt
# Interrupts
## Functions
- Interrupt transfers control to the interrupt service routine generally, through the interrupt vector, which contains the address of all the service routines
- Interrupt architecture must save the address of the interrupted instruction
- A **trap** or **execution** is a software-generated interrupt caused either by an error or a user request
- An OS is **interrupt driven**
	- Meaning it "sleeps" until an interrupt wakes it with something to do.
- Set to user mode to handle interrupts
- Can be done in software or hardware
- ![[Pasted image 20220907102121.png]]
## Interrupt handling
- The OS preserves the state of the CPU by storing registers and the PC
- Determines which type of interrupt has occured:
	- Polling
	- Vectored interrupt system
- Separate segments of code determine what action should be taken for each type of interrupt
- ![[Pasted image 20220907102431.png]]
# Structures
## IO
- After IO starts, control returns to user program only upon IO completion
	- Wait instruction idles the CPU until the next interrupt
	- Wait loop (contention for memory access)
	- At most one IO request is outstanding at a time, no simultaneous IO processing (not true anymore)
- After IO starts, control returns to user program without waiting for IO completion
	- **System Call** - request to the OS to allow user to wait for IO completion
	- **Device-status** contains entry for each IO device indicating its type, address, and state
	- OS indexes into IO device table to determine device status and to modify table entry to include interrupt
## Storage 
- SRAM can be non-volatile
- Main memory - only large storage media that the CPU can access directly
	- random access
	- typically volatile
	- Typically RAM in the form of DRAM
- Secondary storage - extension of main memory that proivdes large nonvolatile storage capacity
- HDD
	- Divided into tracks, which are subdivided into sectors
	- Disk controller determines the logical interaction between the device and the computer
- NVM devices - faster than HDD, nonvolatile
### Hierarchy
- Storage systems organized in hierarchy
	- Speed
	- Cost
	- Volatility
- **Caching**
- **Device Driver**
## Direct Memory Access (DMA)
- Used for high-speed IO devices able to transmit information at close to memory speeds
- Devices controller transfers blocks of data from buffer storage directly to main memory without CPU intervention
- Only one interrupt is generated per block rather than the one interrupt per byte
- can cause problems since it bypasses cache, which can mean that cache won't have updated memory if the DMA is updated
- ![[Pasted image 20220907105159.png]]
# Architecture
## Computer-system
- Most systems use a single general-purpose processor
	- Most systems have special-purpose processors as well
- **Multiprocessors** systems growing in use and importance
	- Also known as parallel systems, or tightly-coupled systems (not really!)
	- Advantages:
		1. **Increased throughput
		2. **Economy of scale
		3. **Increased reliability** - graceful degradation or fault tolerance
	- Two types:
		- **Asymmetric Multiprocessing** - each processor is assigned a specific task
		- **Symmetric Multiprocessing** - each processor performs all tasks
## Clustered Systems3
- Like multiprocessor systems, but multiple systems working together
	- Usually sharing storage via a storage-area network (SAN)
	- Provides a **high-availability** service which survives failures
		- **Assymetric clustering** has one machine in hot-standby mode
		- **Symmetric clustering** has multiple nodes running applications monitoring each other
	- Some clusters are for **high-performance computer (HPC)**
		- Applications must be written to use **parallerization**
	- Some have **distributed lock manager (DLM)** to avoid conflicting operations
# OS Operations
- Bootstrap program - simple code to initialize the system, load the kernel
- Kernel loads
- Starts **System daemons**
- Kernel **interrupt driven** (hardware and software)
	- Hardware interrupt by one of the devices
	- Software interrupt (exception or trap)
- 