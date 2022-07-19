# Class 18: Operating System Essentials
## Processes and Tasks
- ![[Pasted image 20220427173500.png]]
- If a second process, P2, is to be created and run (not shown), then the state of P1 must be saved so it can be later resumed with no side-effects.
	- Since only one copy of the registers exist, they must be saved in memory.
	- We'll see there is hardware support for doing this on the Pentium later.
## Memory
### Hierarchy
- Hierarchy:
	- Cache (SRAMS): Small, expensive, volatile and very fast
	- Main Memory (DRAM): Larger, medium-priced, volatile and medium-speed
	- Disk: GBytes, low-priced non-volatile and slow
- OS is charged with managing these limited resources and creating the illusion of a fast infinitely large main memory
- Memory Manager of the OS:
	- Tracks memory usage
	- Allocates/Deallocates memory.
	- Implements virtual memory.
### Management
- In a multi-programming environment, a simple memory management scheme is to divide up memory in n (possibly unequal) fixed-size partitions. 
==Slide 16 could be on a quiz==
