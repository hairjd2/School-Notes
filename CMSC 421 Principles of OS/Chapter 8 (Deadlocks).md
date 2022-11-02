# System Model
- System consists of resources
- Resource type $R_1$, $R_2$, ..., $R_m$
	- CPU cycles, memory space, I/O devices
- Each resource type $R_i$ has $W_i$
- Each process utilizes a resource as follows:
	- request
	- use
	- release
# Deadlock in Multithread Applications
- Two mutex locks are created and initialized
- ![[Pasted image 20221031102411.png]]
- ![[Pasted image 20221031102425.png]]
- Deadlock is possible if thread 1 acquires `first_mutex` and thread 2 acquires `second_mutex`. Thread 1 then waits for `second_mutex` and thread 2 waits for `first_mutex`.
- Can be illustration
- ![[Pasted image 20221031102556.png]]
- Graph above has a cycle
# Deadlock Characterizations
- Occur only if four characterizations happen simutaneously:
	1. **Mutual exclusion**: only one process at a time can use a resource
	2. **Hold and wait**: a process holding at least one resource is waiting to acquire additional resources held by other processes
	3. **No preemption**: a resource can be released only voluntarily by the process holding it, after that process has completed its task
	4. **Circular wait** there exists a set {P0-Pn} of waiting processes such that P0 is waiting for a resource that is held by P1, P1 is waiting fora resource that is held by P2, Pn-1 is waiting for a resource held by Pn, and Pn is waiting for a resource held by P0
## Resource-Allocation Graph
- A set of vertices V and a set of edges E.
	- V is paritioned into two types:
		1. P = {P1, P2, ..., Pn} the set consisting of all the processes in the system
		2. R = {R1, R2, ..., Rm}, the set consisting of all resource types in the system
	- **Request edge** - directed edge Pi -> Ri
	- **assignment edge** - directed edge Ri -> Pi
## Basic Facts
- If graph contians no cycles => no deadlock
- If graph contains a cycle =>
	- If only one instance per resource type, then deadlock
	- If several instances per resource type, possibility of deadlock (Banker's algorithm)
# Methods for Handling Deadlocks 
- Ensure that the system will **never** enter a deadlock
	- Deadlock prevention
	- Deadlock avoidance
- Allow the sytem to enter a deadlock state and then recover
- Ignore the problem and pretend that deadlocks never occur in the system
# Deadlock Prevention
- **Mutual Exclusion** - not required for sharable resources (e.g. read-only files); must hold for non-sharable resources
- **Hold and Wait** - must guarantee that whenever a process requests a resource, it does not hold any other resources
	- Require process to request and be allocated all its resources before it begins execution, or allow process to request resources only when the process has none allocated to it
	- Low resource utilization; starvation possible
- **No preemption** - We let processes hold and wait, but the minute we run into a resource we can't get the minute its asked for, we roll back and release everything on that process
- **Circular Wait** - impose a total ordering of all resource types and require that process requests resources in an increasing order of enumeration - should use this solution as a programmer
# Deadlock Avoidance
Reqires that the system has some additional **a priori** information available
- Simplest and most useful model requires that each process declare the **max number** of resources of each type that it may need
- algorithm dynamically examines the resource-allocation state to ensure that there can never be a circular-wait condition
- Resource-allocation state is defined by the number of available and allocated resources and the max demands of the processes
## Safe State
- When a process requests an available resource, system must decide if immediate allocation leaves the system in a safe state
- System is in safe state if there exists a sequence of all the processes in the system where for each process, the resources that that process can still request can be satisfied by currentyl available resources + resources held by all the proesses.  
## Basic Facts
- If a system is in a safe state => no deadlocks (currently)
	- This does not mean that a deadlock cannot happen in the future as the system could move into an unsafe state
- If a system is in an unsafe state => possibly of deadlock
	- This does not mean that there necessarily is a deadlock currently, only that the possibility exists.
- Avoidance => ensure that a system will never enter an unsafe state.
## Avoidance Algorithms
- If the system has only a single instanec of each resource type:
	- Use a resource-allocation graph
- If the system has multiple instances of any resource types
	- Use the Banker's Algorithm
## Resource-Allocation Graph Scheme
- **Claim edge** Pi -> Ri indicated that process Pj may request resource Rjl represented by a dashed line
- A claim edge converts to a request edge when a process requests a resource
- A request edge is converted to an assignment edge when the resource is allocated to the process
- When a resouce is released by a process, assignment edge reconverts to a claim edge
	- Represents that the resource may still be requested again by the process in the future
- Resources must be claimed *a priori* in the system
- ![[Pasted image 20221102102117.png]]
- ![[Pasted image 20221102102154.png]]
### Resource-Allocation Graph Algorithm
- Suppose that process Pi requests a resource Rj
- The request can be granted only if converting the request edge to an assignment edge does not result in the formation of a cycle in the resource allocation graph
	- Even if the cycle involves a dashed line
## Banker's Algorithm (Important to know for tests)
- Multiple instances of resources
- Each process must a priori claim max use
- When a process requests a resource it may have to wait
- When a process gets all its resources it must return them in a finite amount of time
### Data Structures for the Algorithm from Banker
- Let n = number of processes, and m = number of resource types.
	- **Available**: Vector of length m. If available [j] = k, there are k instances of resource type Rj available
	- **Max**: n x m matrix. If Max[i, j] = k, then process Pi may request at most k instances of resource type Rj
	- **Allocation**: n x m matrix. If Allocation[i, j] = k then Pi is currently allocated k instances of Rj
	- **Need**: n x m matrix. If Need[i, j] = k, then Pi may need k more instances of Rj to complete its task
- Need[i, j] = Max[i, j] - Allocation[i, j]
### Safety Algorithm
1. Let **Work** and **Finish** be vectors of length m and n, respectively. Initialize:
	1. Work = Available
	2. Finish[i] = false for i = 0, 1, ..., n-1
2. Find an i such that both:
	1. Finish[i] = false
	2. Need_i <= Work
	3. If no such i exists, go to step 4
3. Work = Work + allocationi; Finish[i] = true; go to to step 2
4. If Finish[i] = true for all i, then the system is in a safe state
### Resource-Request Algorithm for Process Pi
- ![[Pasted image 20221102104511.png]]
# Deadlock Detection

# Recovery from Deadlock