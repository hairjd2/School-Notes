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
- ![[Pasted image 20221005102133.png]]
### One-to-One
- Each user-level thread maps to a kernel thread
- Creating a user-level thread creates a kernel thread
- More concurrency than many-to-one
- Number of threads per process sometimes restricted due to overhead
- Windows and Linux
- ![[Pasted image 20221005102152.png]]
### Many-to-Many
- Allows many user level threads to be mapped to many kernel threads
- Allows the OS to create a sufficient number of kernel threads
- Windows with the *ThreadFiber* package
- Otherwise not very common
- ![[Pasted image 20221005102210.png]]
### Two-level Model
- Similar to M:M, except that it allows a user thread to be bound to a kernel thread
- ![[Pasted image 20221005102437.png]]
## Thread Libraries
- provides programmer with API for creating and managing threads
- Two primary ways of implementing
	- Library entirely in user space
	- Kernel-level library supported by the OS
- Thread libraries include:
	- Pthreads (POSIX-like systems, including: Linux, Mac, iOS, Android)
	- Windows threads
	- Java threads
### Pthreads
- May be provied as user-level or kernel-level
- A POSIX standard (IEEE 1003.1c) API for thread creation and synchronization
- Specification, not implementation
- API specifies behavior of the thread library, implementation is up to development of the library
- Common in UNIX-like OSes (Linux, Mac OS X, BSD)
## Implicit Threading
- Growing in popularity as numbers of threads increase, program correctness more difficult with explicit threads
- Creation and management of threads done by compilers and run-time libraries rather than programmers
- Four methods explored
	- Thread pools
	- OpenMP
	- Grand Central Dispatch
	- Intel Threading Building Blocks
### Thread Pools
- Create a number of threads in a pool where they await work
- Advantages:
	- Usually slightly faster to service a request with an existing thread than create a new thread
	- Allows the number of threads in the application(s) to be bound to the size of the pool
	- Separating task to be performed from mechanics of creating task allows different strategies for running task
		- i.e. Tasks could be scheduled to run periodically
- Windows API supports thread pools:
### OpenMP
- Set for compiler directives and an API for C, C++, FORTRAN
- Provides support for parallel programming in shard-memory environments
- Identifies **parallel regions** - blocks of code that can run in parallel
- ```
``` C
#pragma omp parallel
```
- Create as many threads as there are cores
- Run the for loop in parallel
``` C
#pragma omp parallel
for (i = 0; i < N; i++) {
	c[i] = a[i] + b[i];
}
```
### Grand Central Dispatch
- Apple technology for Mac OS X and iOS OSes
- Extensions to C, C++ and Objective-C languages, API, and run-time library
- Allows identification of parallel sections
- Manages most of the details of threading
- Block is in "^{}"
```C
^{printf("I am a block");}
```
- Blocks placed in dispatch queue: assigned to available thread in thread pool when removed from queue
- Two types of dispatch queues:
	- **Serial** - blocks removed in FIFO order, queue is per process, called **main queue**
		- Programmers can create additional serial queues within program
	- **Concurrent** - removed in FIFO order but several may be removed at a time
- For the Swift language a task is defined as a closure - similar to a block minus the caret
- Closures are submitted to the queue using the `dispatch_async()` function
### Intel Threading Building Blocks (TBB)
- Template library for designing parallel C++ programs
- A serial version of a simple for loop
```C++
for(int i = 0; i < n; i++) {
	apply(v[i]);
}
```
- The same loop written using TBB with `parallel_for` statement
## Threading Issues
- Semantics of `fork()` and `exec()` syscalls
- Signal handling: synch or asynch
- Thread cancellation of target thread: asynch or deferred
- Thread-local storage
- Scheduler Activations
### Semantics of `fork()` and `exec()`
- Does `fork()` duplicate only the calling thread or all threads?
	- Some UNIX-like systems have two versions of fork
- `exec()` usually works as normal - replace the running process including all threads
### Signal Handling
- **Signals** are used in UNIX-like systems to notify a process that a particular event has occurred
- A **signal handler** is used to process signals
	- Signal is generated by particular event
	- Signal is delivered to a process
	- Signal is handled by one of two signal handlers
		- Default
		- User-defined
- Every signal has **default handler** that kernel runs when handling signal (usually just kills the process)
	- **User-defined signal handler** can override default
	- For single-threaded, signal delivered to process
- Where should a signal be delivered for multi-threaded?
	- Deliver the signal to the thread to which the signal applies
	- Deliver the signal to every thread in the process
	- Deliver the signal to certain threads in the process
	- Assign a specific thread to receive all signals for the process
### Thread Cancellation
- Terminating a thread before it has finished
- Thread to be cancelled is **target thread**
- Two general approaches
	- *Asynch cancellation* terminates the target thread immediately
	- *Deferred cancellation* - allows the target thread to periodically check if it should be cancelled
- Pthread code to create and cancel a thread:
```C
pthread_t tid;

/* create the thread */
pthread_create(&tid, 0, worker, NULL);
 . . .

/* create the thread */
pthread_cancel(tid);

/* wait for the thread to terminate */
pthread_join(tid, NULL);
```
- Invoking thread cancellation requests cancellation, but actual cancellation dependsd on thread state
- If thread has cancellation disabled, cancellation remains pending until thread enables it
- Default type is deferred
	- Cancellation only occurs when thread reaches **cancellation point**
		- i.e. `pthread_testcancel()`
		- Then **cleanup handler** is invoked
- On Linux systems, thread cancellation is handled through signals
### Thread-Local Storage
- **Thread-local storage (TLS)** allows each thread to have its own copy of data
- Useful when you do not have control over the thread creation process (like using a thread pool)
- Different from local variables
	- Local variables visible only during single function invocation
	- TLS visible acress function invocations
- Similar to `static` data
	- TLS is unique to each thread
	- Identified by a special language keyword (`thread_local` in C11 and C++11)
### Scheduler Activations
- Both M:M and Two-level models require communication to maintain the appropriate number of kernel threads allocated to the application
- Typically use an intermediate data structure between user and kernel threads - **lightweight process (LWP)**
	- Appears to be a virtual processor on which process can schedule user thread to run
	- Each LWP attached to kernel thread
	- How many LWPs to create?
- Scheduler activations provide **upcalls** - a communication mechanism from the kernel to the **upall handler** in the thread library
- This communication allows an application to maintain the correct number kernel threads
## OS Examples