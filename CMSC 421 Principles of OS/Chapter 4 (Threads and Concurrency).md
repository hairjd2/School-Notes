# Chapter 4: Threads and Concurrency
## Overview
- Most modern applications are multithreaded
- Threads run within one process
- Can simplify code, increase efficiency
- Responsiveness - may allow continued execution if part of process is blocked
- Resource sharing - threads share resources of process easier than shared memory or message passing
- Economy - cheaper than process creation, thread switching lower overhead than context switching
- Scalability - process can take advantage of multicore architectures
## Multicore Programming
- **Multicore** or **multiprocessor** systems put pressure on programmers challenges include:
	- Dividing activities
	- Balance
	- Data splitting
	- Data dependency
	- Testing and debugging
- ![[Pasted image 20221003105612.png]]
### Parallelism
- *Parallelism* implies a system can perform more than one task simulataneously
- Types:
	- **Data parallelism** - distributes subsets of the same data across multiple cores, same operation on each
	- **Task parallelism** - distributing threads across cores, each thread performing unique operation
- ![[Pasted image 20221003110044.png]]
### Concurrency
- *Concurrency* suppports more than one task making progress
	- Single processor/core, scheduler providing concurrency
### Amdahl's Law
- Identifies performance gains from adding additional cores to an application that has both serial and parallel components
- S is serial portion
- N processing cores 
- $speedup\le\frac{1}{S+\frac{(1-S)}{N}}$
- That is, if application is 75% parallel / 25% serial, moving from 1 to 2 cores results in speedup of 1.6 times
- As N approaches infinity, speedup approaches 1/S
- But does the law take into account contemporary multicore systems
- ![[Pasted image 20221003110454.png]]
### User and Kernel Threads
- **User threads** - management done by user-level threads library
- **Kernel threads** - Supported by the kernel
	- Examples - virtually all general purpose OSes, including:
		- Windows
		- Linux
		- Mac OS
## Multithreading Models
### Many-to-one
- Many user-level threads mapped to single kernel thread
- One thread blocking causes all to block
- Multiple threads may not run in parallel on multicore system because only oen may be in kernel at a time
- Few systems currently use this model
- When one thread needs to block, it blocks the kernel thread, meaning all threads need to block
### One-to-One
- Each user-level thread maps to a kernel thread
- Creating a user-level thread creates a kernel thread
- More concurrency than many-to-one
- Number of threads per process sometimes restricted due to overhead
- Windows and Linux
### Many-to-Many
- Allows many user level threads to be mapped to many kernel threads
- Allows the OS to create a sufficient number of kernel threads
- Windows with the *ThreadFiber* package
- Otherwise not very common
## Thread Libraries
## Implicit Threading
## Threading Issues
## OS Examples