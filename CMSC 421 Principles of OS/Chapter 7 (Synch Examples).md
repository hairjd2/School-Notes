# Classical Problems of Synchronization
## Bounded-Buffer Problem
- n buffers, each can hold one item
- Semaphore `mutex` initialized to 1
- Semaphore `full` initialized to 0
- Semaphore `empty` initialized to n
- ![[Pasted image 20221026104059.png]]
- ![[Pasted image 20221026104120.png]]
- wait dec, signal inc
## Readers and Writers Problem
- A data set is shared among a number of concurrent processes
	- **Readers** - only read the data set; they do not perform any updates
	- **Writers** - can both read and write
- Problem - allow multiple readers to read at the same time
	- Only one single writer can access the shared data at the same time
- Several variations of how readers and writers are considered - all involve some form of priorities
- Shared data
	- Data set
	- Semaphore `rw_mutex` initialized to 1
	- Semaphore `mutex` initialized to 1
	- Integer `read_count` initialized to 0
- ![[Pasted image 20221026104801.png]]
- ![[Pasted image 20221026104833.png]]
### Readers-Writers Problem Variations
- **First** variation - no reader kept waiting unless writer has permission to use shared object
- **Second** variation - once writer is ready, it performs the write ASAP
- Both may have starvation leading to even more variations
- Problem is solved on some systems by kernel providing reader-writer locks
## Dining-Philosophers Problem
- Philosophers spend their lives alternating thinking and eating
- Don't interact with their neighbors, ocassionally try to pick up 2 chopsticks (one at a time) to eat from bowl
	- Need both to eat, then release both when done
- In the case of 5 philosophers
	- Shared data
		- Bowl of rice (data set)
		- Semaphore `chopstick[5]` initialized to 1
- ![[Pasted image 20221026110312.png]]
- This will deadlock if all phiolosophers pick up the chopstick on their right
- ![[Pasted image 20221026110345.png]]
- ![[Pasted image 20221026110629.png]]
- Each Philosopher i invokes the ops `pickup()` and `putdown()` in the following sequence:
	- ```DiningPhilosophers.pickup(i);
	  /** EAT **/
	  DiningPhilosophers.putdown(i);```
-  No deadlock, but starvation is possible
# Kernel Synch - Windows
- Uses interrupt masks to protect access to global resources on uniprocessor systems
- Uses **spinlocks** on multiprocessor systems
	- Spinlocking-thread will never be preempted
- Also provides **dispatcher objects** user-land which may act mutexes, semaphores, events, and timers
	- **Events** 
		- Acts much like a condition variable
	- TImers notify one or more thread when time expired
	- Dispatcher objects either **signaled-state** (object available) or **non-signaled state** (thread will block)
# Linux Synch
- Linux:
	- Prior to kernel version 2.6, disables interrupts (and thus preemption) to implement short critical sections
	- Version 2.6 and later, fully preemptive
- Linux provides:
	- Semaphores
	- spinlocks
	- reader-writer versions of both
	- atomic integers
- On a single-CPU system, spinlocks are replaced by enabling and disabling kernel preemption
- Atomic variables
	- `atomic_t` is the type for an atomic integer
- Consider the variables
	- `atomic_t counter;`
	- `int value;`