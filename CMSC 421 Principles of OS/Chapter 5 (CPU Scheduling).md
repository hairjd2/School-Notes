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
## Multi-Processor Scheduling
## Real-Time CPU Scheduling
## OS Examples
## Algorithm Evaluation
