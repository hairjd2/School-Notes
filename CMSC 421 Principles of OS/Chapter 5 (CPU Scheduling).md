# Chapter 5: CPU Scheduling
## Basic Concepts
- Job is to maximize CPU utilization
- CPU-I/O Burst Cycle - Process execution consists of a **cycle** of CPU execution and I/O wait
- **CPU burst** (when its actually doing something useful) followed by **I/O burst** (when its waiting for something from the related I/O).
- **I/O bursts** take up the most time
### CPU Scheduler
- Selects from among the processes in ready queue, and allocates a CPU core to one of them
- CPU Scheduling decisions may take place when a process:
	1. Switches from running to waiting state
	2. Switches from running to ready state
	3. Switches from waiting to ready
	4. Terminates
- Scheduling under only 1 and 3 above is **nonpreemptive** or **cooperative**
- All other scheduling is **preemptive**
	- Consider access to shared data - need to worry about synchronization
	- Consider preemption while in kernel mode
	- Consider interrupts occurring during crucial OS activities - can disable interrupts (bad idea for a real-time system)
- All use preemptive scheduling in general purpose systems
### Dispatcher
- Dispatcher module gives control of the CPU to the process selected by the short-term scheduler; this involves:
	- Switching context
	- Switching to user mode
	- Jumping ot the proper location in the user program to restart that program
- **Dispatch latency** - time it takes for the dispatcher to stop one process and start another running - wanna reduce this as much as possible
## Scheduling Criteria
- **CPU utilization** - keep the CPU as busy as possible
- **Throughput** - # of processes that complete their execution per time unit
- **Turnaround time** - amount of time to execute a particular process
- **Waiting time** - amount of time to execute a particular process
- **Response time** - amount of time it takes from when a request was submitted until the first response is produced, not output (for time-sharing environment)
## Scheduling Algorithms
### First- Come, First-Served (FCFS) Scheduling
- ![[Pasted image 20221010102856.png]]
- ![[Pasted image 20221010103052.png]]
- Nonpreemptive
### Shortest-Job-First (SJF) Scheduling
- Associate with each process the length of its next CPU burst
	- Use these lengths to schedule the process with the shortest time
- SJF is optimal - gives minimum average waiting time for a given set of processes
	- The difficulty is knowing the length of the next CPU request
	- Could ask the user
- Also nonpreemptive
- Only best when you actually know the correct burst time of each process (usually need to see the future)
- ![[Pasted image 20221010104051.png]]
### Round Robin (RR)
- Each process gets a small unit of CPU time (**time quantuum** q), usually 10-100ms. After this time has elapsed, the process is preempted and added to the end of the ready queue.
- If there are n processes in the ready queue and the time quantuum is q, then each process gets 1/n of the CPU time in chunks of at most q time units at once. No process waits more than (n-1)q time units
- Timer interrupts every quantum to schedule next process
- Performance
	- q large => FCFS
	- q small => q must be large with respect to context switch, otherwise more time is being wasted doing context switching than actually doing "useful stuff"
- ![[Pasted image 20221010105324.png]]
- preemptive FCFS
- Want 80% of CPU bursts to be shorter than q
- Each process gets its own time, even if the previous process had remaining time
### Priority Scheduling
- A priority number (integer) is associated with each process
- The CPU is allocated to the process with the highest priority (smallest integer = highest priority, generally)
	- Can be done either in a preemptive or non-preemptive manner
- SJF is priority scheduling where priority is the inverse of predicted next CPU burst time
- Problem: **Starvation** - low priority processes may never execute
	- Solution: **Aging** - as time progresses increase the priority of the process
	- This way low priority processes will actually become high priority
### Priority Scheduling w/ RR
- Run the process with the highest priority. Processes with the same priority run RR
- check slide 23
## Thread Scheduling
- Distinction between user-level and kernel-level threads
- When threads supported in a kernel, threads are what is scheduled, not processes
- In the m:o and m:m models, thread library schedules user-level threads to run on LWP
## Multi-Processor Scheduling
- CPU scheduling more complex when multiple CPUs are available
- Multiprocess may be any one of the following architectures
	- Multicore CPUs
	- Multithreaded cores
	- NUMA systems
	- Heterogeneous multiprocessing
- In a **Symmetric Multiprocessing System** (SMP), in general threads are eligible to run on all cores or CPUs since each core/CPU is symmetric
- All threads may be in a common ready queue (a)
- Each processor may have its own private queue of threads (b)
### Multicore Processors
- Recent trend to place multiple processor cores on same physical chip
- Faster and consumes less power
- Multiple threads per core also growing
	- Takes advantage of memory stall to make progress on another thread while memory retrieve happens
### Multithreaded Multicore System
- In a system with multiple hardware threads per core, If one thread has a memory stall, switch to another thread!
- **Chip-multithreading** (CMT) assigns each core multiple hardware threads (Intel refers to this as hyperthreading)
- On a quad-core system with 2 hardware threads per core, the OS sees 8 logical processors
- Two levels of scheduling
	1. The OS deciding which software thread to run on a logical CPU
	2. How each core decides which hardware thread to run on the physical core
### Load Balancing
- If SMP, need to keep all CPUs loaded for efficiency 
- **Load Balancing** attempts to keep workload evenly distributed
- **Push Migration** - periodic task checks load on each processor, and if found pushes task from overloaded CPU to other CPUs
- **Pull Migration** - idle processors pulls waiting task from busy processor
### Processor Affinity
- Basically says "this thread should run on this CPU"
- When a thread has been running on one processor, the cache contents of that processor stores the memory accesses by that thread
- We refer to this as a thread having affinity for a processor (i.e. "processor affinity")
- Load balancing may affect processor affinity as a thread may be moved from one processor to anotherr to balance loads, yet that thread loses the contents of what it had in the cache of the processor it was moved off of
- **Soft Affinity** - the OS attempts to keep a thread running on the same processor but no guarantees
- **Hard affinity** - allows process to specify a set of processors it may run on
### NUMA and CPU Scheduling
- If the OS is NUMA-aware, it will assign memory closest to the CPU the thread is running on.
## Real-Time CPU Scheduling
- Can present obvious challenges
- **Soft real-time systems** - Critical real-time tasks have the highest priority, but no guarantee as to when the tasks will be scheduled
- **Hard real-time systems** - task must be serviced by its deadline
- **Event latency** - the amount of time that happens between when an event happens and when it is dealt with
	1. **Interrupt latency** - how long from when an interrupt occurs to when it is dealt with
	2. **Dispatch latency** - time for schedule to take current process off CPU and switch to another
### Priority-based Scheduling
- For real-time scheduling, scheduler must support preemptive, priority-based scheduling
	- But only guarantees soft real-time
- For hard real-time must also provide ability to meet deadlines
- Processes have new characteristics: **periodic** ones requre CPU at constant intervals
	- Has processing time t, deadline d, period p
	- $0 \le t \le d \le p$
	- Rate of periodic task is 1/p
## OS Examples
- Linux through version 2.5 used a round robin scheduler, which was great for soft real-time systems but awful for interaction
- Linux version 2.6.23+ uses CFS (**Completely Fair Scheduler**)
	- Supports load-balancing and is NUMA-aware
- Windows uses priority-based preemptive scheduling
	- **Dispatcher** is scheduler
	- **Variable class** is 1-15, **real-time class** is 16-31
	- If no run-able thread, runs **idle thread**
	- Most things have a priority of 8
	- slide 57 should say "+3 priority boost" instead of "3x priority boost"
## Algorithm Evaluation
- How to select CPU-scheduling algorithm for an OS?
- Determine criteria, then evaluate algorithms
- **Deterministic modeling**
	- Type of **analytic evaluation**
	- Takes a particular predetermined workload and defines the performance of each algorithm for that workload
- Consider 5 processes arriving at time 0
- 