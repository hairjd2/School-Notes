# Background
- Code needs to be in memory to execute, but entire program rarely used
	- Error code, unusual routines, large data structures
- Entire program code not needed at same time
- Consider ability to execute partially-loaded program
	- Program no longer constrained by limits of physical memory
	- Each program takes less memory while running -> more programs run at the same time
		- Increased CPU utilization and throughput with no increase in response time or turnaround time
	- Less I/O needed to load or swap programs into memory -> each user program runs faster
## Virtual Memory
- **Virtual memory** - separation of user logical memory from physical memory
	- Only part of the program needs to be in memory for execution
	- Logical address space can therefore be much larger than physical address space
	- Allows address spaces to be shared by several processes
	- Allows for more efficient process creation
	- More programs running concurrently
	- Less I/O needed to load or swap processes
- **Virtual address space** - logical view of how process is stored in memory
	- Usually start at a low address (maybe even 0), contiguous addresses until end of space
	- Meanwhile, physical memory organized in page frames
	- MMU must map logical to physical
- Virtual memory can be implemented via: 
	- Demand paging
	- Demand segmentation
## Virtual-address Space
- Usually design logical address space for stack to start at Max logical address and grow "down" while heap grows "up"
	- Maximises address space use
	- Unused address space between the two is hole
		- No physical memory needed until heap or stack grows to a given new page
- Enables **sparse** address spaces with holes left for growth, dynamically linked libraries, etc. 
- System libraries via mapping into virtual address space
- Shared memory by mapping pages read-write into virtual address space
- Pages can be shared during `fork()`, speeding processes creation
# Demand Paging
- Could bring entire process into memory at load time
- Or bring a page into memory only when it is needed
	- Less I/O needed, no unnecessary I/O
	- Less memory needed
	- Faster response
	- More users
- Similar to paging system with swapping
- Page is needed => reference to it
	- Invaild reference => abort
	- not-in-memory => bring to memory
- **Lazt swapper** - never swaps a page into memory unless page will be needed
	- Swapper that deals with pages is a **pager**
- Could bring entire process into memory at load time
- Or bring a page into memory only when it is needed
	- Less I/O needed, no unnecessary I/O
	- Less memory needed
	- Faster response
	- More users
- Similar to paging system with swapping (diagram below)
- ![[Pasted image 20221116103002.png]]
## Basic Concepts
- With swapping, pager guesses which pages will be used before swapping out again
- Instead, pager brings in only those pages into memory
- How to determine that set of pages?
	- Need new MMU functionality to implement demand paging
- If pages needed are already **memory resident**
	- No difference from non demand-paging
- If page needed and not memory resident
	- Needed to detect and load the page into memory from storage
		- Without changing program behavior
		- Without programmer needing to change code
## Valid-Invalid Bit
- WIth each page table entry a valid-invalid bit is associated (v => in-memory - **memory resident**, i => not-in-memory)
- Initially valid-invalid bit is set to i on all entries
- ![[Pasted image 20221116103418.png]]
- During MMU address translation, if valid-invalid bit in page table entry is i => 
## Steps in Handling Page Fault
1. If there is a reference to a page, first reference to that page will trap to operating system
	1. Page Fault
2. Operating system looks at another table to decide:
	1. invalid reference => abort
	2. Just not in memory
3. Find free frame
4. Swap page into frame via scheduled disk operating
5. Reset tables to indicate page now in memory Set page valid bit = v
6. Restart the instruction that caused the page fault
- ![[Pasted image 20221116103646.png]]
# Aspects of Demand Paging
- Extreme case - start process with no pages in memory
	- OS sets instruction pointer to first instruction of process, non-memory-resident -> page fault
	- And for every other process pages on first access
	- **Pure demand paging**
- Actually, a given instruction could access multiple pages -> multiple page faults
	- Consider fetch and decode of instruction which adds 2 numbers from memory and stores result back to memory
	- Pain decreased because of **locality of reference**
- Hardware support needed for demand paging
	- Page table with valid/invalid bit
	- Secondary memory (swap device with **swap space**)
	- Instruction restart
## Instruction Restart
- Consider an instruction that could access several different locations
	- Block move
	- ![[Pasted image 20221116104027.png]]
	- Auto increment/decrement location
	- Restart the whole operation?
		- What if source and destination overlap?
## Free-Frame List
- When a page fault occurs, the operating system must bring the desired page from secondary storage into main memory.
- Most operating systems maintain a **free-frame list** -- a pool of free frames for satisfying such requests
- Operating system typically allocate free frames using a technique known as **zero-fill-on-demand** -- the content of the frames zeroed-out before being allocated
- When a system starts up, all available is placed on the free-frame list.
## Stages in demand paging - worse case
1. Trap to the OS
2. Save the user registers and process state
3. Determine that the interrupt was a page fault
4. Check that the page reference was legal and determine the location of the page on the disk
5. Issue a read from the disk to a free frame:
	1. Wait in a queue for this device until the read request is serviced
	2. Wait for the device seek and/or latency time
	3. Begin the transfer of the page to a free frame
6. While waiting, allocate the CPU to some other user
7. Receive an interrupt from the disk I/O subsystem (I/O completed)
8. Save the registers and process state for the other user
9. Determine that the interrupt was from the disk
10. Correct the page table and other tables to show page is now in memory
11. Wait for the CPU to be allocated to this process again
12. Restore the user registers, process state, and new page table, and then resume the interrupted instruction
## Demand Optimization
- Not in slides:
	- Can also have a two-level system
	- Allocate some of your swap space as normal space
	- Allocate some of your swap space as compressed space
	- 
# Copy-on-Write
- Allows both parent and child prcoesses to initially share the same pages in memory
	- If either process modifies a shared page, only then is the page copied
- COW allows more efficient process creation as only modified pages are copied
- 
# Page Replacement
# Allocation of Frames
# Thrashing
# Memory-Mapped Files
# Allocating Kernel Memory
# Other Considerations
# Operating-System Examples
