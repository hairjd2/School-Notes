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
- 