# Class 9: Memory Hierarchy and Caches
## Memory Hierarchy
- Computer pioneers correctly predicted that programmers wanted unlimited fast memory 
- An economical solution to this was to create memory hierarchy 
	- Multiple levels of memories as the distance from the processor grows 
- This hierarchy is based off the idea of locality 
	- Locality states that computers do not access all code or data uniformly
- Memory hierarchy exploits locality to provie large, fast and inexpensive memory
- ![[Pasted image 20220622200637.png]]
### Static Random Access Memory (SRAM)
- ![[Pasted image 20220622201241.png]]
- Volatile memory used mainly for registers and L1 and L2 caches 
	- volatile memory loses its charge when it loses power 
- Each bit consists of 6 transistors 
	- Making it fast and stable 
- Static 
	- Does not need a refresh
### Dynamic Random Access Memory (DRAM)
- ![[Pasted image 20220622201450.png]]
- Volatile memory used mainly for the main memory 
- Each bit is made of a transistor and capacitor 
- Can be more dense than SRAM 
- Dynamic: needs to be refreshed as the capacitor loses charge 
	- Leads to it being slower than SRAM
### Hard Disk Drive (HDD)
- Introduced in 1956 by IBM<
	- IBM 350 RAMAC disk storage unit with a whopping 3.75MD
- Mechanical device used for large storage
	- Data stored on magnetic material
	- Mechincal nature makes it slow
	- It is slowly being replaced by SSD
	- Non-volatile memory
### Flash
- Developed by Toshiba in 1980s 
- Based on EEPROM memory (electrically erasable programable read only memory) 
	- EEPROM requires the entire memory to be erased before reuse 
	- Flash allows erasing and rewriting in blocks 
- Comes in two main configurations 
	- NOR Flash 
		- Erases and writes data in byte chunks 
	- NAND Flash 
		- Writes and erases data in larger blocks (multiple bytes) 
- Non-Volatile 
- Used in USB flash drives, SSD 
- Wears out faster than other memories
## Cache
- Use library analogy to say that once you get the book, you leave the book at your desk instead of putting it back then getting it again
- High speed memory between CPU and Main Memory
- Takes advantage of locality to improve memory performance
- Locality states that computers do not access memory uniformly
	- Temporal locality
		- You will probably need to access that data again (library)
	- Spatial locality
		- You will probably need the data around that data soon
- When the requested data is found in the cache it is a cache hit
- When the data is not found it is a cache miss
	- A fixed size of the data containing the requested word (block) is then fetched from the main memoryu and put in the cache
	- A miss causes in order execution to stall
	- For out of order the other instructions can execute while the one that needs it stalls
### Policy
- Four common questions have to be answered when caching:
	1. Where can a block be placed? (block placement)
	2. How is a block found? (block identification)
	3. Which block is replaced on a miss? (block replacement)
	4. What happens on a write? (write strategy)
- This policy applies to the memory hierarchy in general
#### Block Placement
- Direct mapped:
	- Block can only be placed in one place in the cache
	- Chosen by Block address MOD # of blocks in cache
- Fully Associative:
	- Block can be placed anywhere in the cache
- Set Associative:
	- Can be placed in a restricted set of places (blocks) in the cache
	- Chosen by Block address MOD # of sets
	- N blocks in a set makes n-way set associative
		- Direct mapped is one way set associative
- ![[Pasted image 20220622233520.png]]
#### Block Identification
- Memory address is separated into 3 pieces
- Block offset selects the data inside the block
- Index is used to pixk the cache set
- Tag is the remainder used to identify a particular block for a hit
	- Tag grows with associativity
	- Fully associative has a large tag and no index
- ![[Pasted image 20220622233637.png]]
- ![[Pasted image 20220622233804.png]]
#### Block Replacement
- When a miss occurs a block has to be removed to make space for the new block
- With direct mapped the block in the current space is replaced
- With set associativbe a decision has to be made:
	- Random: candidate blocks are randomly chosen
	- Least Recently Used (LRU): Access to blocks are recorded and the block least recently accessed is thrown out
	- First in First Out (FIFO): LRU can be complicated this approximates LRU by kicking out the oldest block
- As number of blocks increase LRU becomes more complicated
- A common method called Pseudo LRU is used to approximate LRU
	- Each way has a bit corresponding to it
	- When the set is accessed that bit is turned on
	- When all bits are on, they are reset to 0 save except for the one most recently accessed
	- The way whose bit is 0 is chosen for replacement
#### Write Strategy
- Two options when writing to memory:
	- Write through: data is written to both the block in the cache and the block in memory
	- Write back: data is written to just the block in the cache
		- The modified block is written back to memory when it is replaced
		- To reduce the frequency of write backs, a dirty bit is used 
			- Marks the block as dirty when it gets written to
- Each strategy has its advantages:
	- Write through:
		- Easier to implement
		- Lower level is always updated
	- Write back:
		- Multiple writes to upper level result in one write to lower level
- Write through results in write stalls as we wait for the cache to process writes
- We can add a write buffer
	- Allows the processor to proceed as soon as data is written to the buffer
	- Reduces but does not completely get rid of stalls
### Performance
- Hit rate: percentage of memory accesses that result in a hit
- Miss rate: percentage of memory access that result in a miss
- Miss rate + hit rate = 100%
- A good gauge for performance is the Average Memory Access Time (AMAT)
- AMAT = T_hit + Miss Rate * T_miss penalty
- Where:
	- T_hit: Time it takes for a hit in the cache
		- Constraints clock rate
	- Miss rate: miss rate in the cache
	- T_miss penalty: Time spent finding the data and bringing into the cache
		- We will assume an in-order processor
		- Stalls due to memory are strictly from misses
- Cache performance impacts CPU performance
- Recall:
	- CPU time = IC x CPI x Clock cycle time
	- Adding the effect of cache misses:
		- ![[Pasted image 20220622235458.png]]
#### Example
- ![[Pasted image 20220622235521.png]]
- ![[Pasted image 20220622235601.png]]
- ![[Pasted image 20220622235639.png]]
#### Miss Penalty in OoO
- In an out of order processor the miss penalty is not always exposed
- Due to the out of order nature other instructions can utilize the stall cycles
- This changes how we calculate CPU performance
	- We only consider the stall cycles that are exposed
##### Example
- ![[Pasted image 20220622235848.png]]
- ![[Pasted image 20220622235910.png]]
### Optimization
- AMAT = T_hit + Miss Rate * T_miss penalty
- Based off the AMAT formula we can group the basic cache optimization techniques into 3 categories
	- Reducing miss rate:
		- Larger cache/block size, higher associativity
	- Reducing miss penalty
		- Multilevel caches and giving reads priority over writes
	- Reducing time to hit in the cache
		- Avoiding address translation when indexing cache
- ![[Pasted image 20220623001911.png]]
#### Cache Misses
- Four types of cache misses
	1. Compulsory: First reference to a block will not exist in the cache
	2. Capacity: when cache cannot hold all blocks, they will be discarded and later retrieved
	3. Conflict: program makes references to multiple addresses from different blocks that refer to the same location
	4. Coherence miss: cache flushes to keep multiple caches coherent in a multiprocessor
#### Large Block Sizes
- Simplest way to decrease miss rate
- Takes advantage of spatial locality
	- Reduces compulsory misses
- However, increases miss penalty
	- Arising from larger transfer times
- For the same size cache;
	- Larger blocks, means less blocks
	- Increasing conflict and capacity misses
#### Larger Cache
- Reduces capacity misses
- However, potentially longer hit time
	- Caches are smaller to increase speed so larger caches are moving away from this
- Higher cost and power
	- Increase in area as well
#### Higher Associativity
- Higher associativity reduces conflict misses
	- Full associativity allows data to reside anywhere
- Higher associativity increases hit time
	- More possibilities to search through
#### Multilevel Caches
- Higher level caches are usually small and have low associativity
	- Better hit time
	- High miss rate
- You can add slightly bigger caches as you move further away from the chip
	- Have larger size and associativity to decrease misses
	- Decreases time spent off chip
#### Multilevel Performance
- With multilevel caches the T_miss penalty encompasses the AMAT of lower levels
- Assuming L1 and L2 cache
	- AMAT_L1 = T_hitL1 + Miss Rate_L1 * T_miss penalty L1
		- T_miss penalty L1 = T_hit L2 + Miss Rate_L2 * T_miss penaltyL2
#### Inclusion/Exclusion
- When data is placed in the first level, should it also be placed in the second level?
- Typically, yes (inclusion)
	- Inclusion states that a block present in L1 is also present in L2
	- To check for a hit just check L2
	- Makes checking consistency in multi processors easier
	- This does reduce the capacity for the multi level cache
- Alternatively swap blocks out (exclusion)
	- No block in L1 is in L2
	- Swap blocks on a L1 miss/L2 Hit
	- You have to search the whole hierarchy
#### Miss/Write Priority
- The next optimization is to give priority to read misses over writes
- Read misses are more likely to cause stalls in program execution than writes
	- Delaying a read has more impact on performance than a write
- Giving misses priority over writes reduces the impact of misses on performance
	- Using a write buffer helps in implementing this, however, it must be check for data that might not have been written yet
## Virtual Memory
- Virtual memory divides physical memory into blocks and allocates them to processes
	- At any given time a processor has multiple processes running
	- Virtual memory ensures efficient use of memory by processes
- Processes must be restricted to acceessing only thier blocks
- Virtual memory was invented to ensure that programs did not try to access more memory than available
	- Physical memory might be too small
	- It automatically manages the two levels of the memory hierarchy represented by main memory and secondary storage (disk/ssd)
	- Allows programs to store data in different locations
- ![[Pasted image 20220623003624.png]]
### Virtual Memory vs. Cache
- Virtual memory shares a lot of the same ideas as cache
- A block in VM is referred to as page/segment
	- Pages are fixed size blocks at 4096 to 8192 bytes
	- Segments are variable sized blocks
- Page fault or address fault in VM is a miss
- ![[Pasted image 20220623003811.png]]
- VM Virtual addresses:
	- Produced by processor
	- Translated to physical address with access to main memory
		- Done by a combination of hardware and software
- Replacement on a miss is handled by:
	- Hardware for a cache
	- OS for VM
- Processor address size determines size of VM
	- Cache size is independent of processor address size
### Page vs. Segment
- Decision to use pages vs segments affects the processor
	- Page addressing is a single fixed address
		- Divided into page number and offset within page (similar to cache addressing)
	- Segments require 2 words for address
		- 1 word for segment number
		- 1 word for offset within segment
- ![[Pasted image 20220623004215.png]]
### Four Hierarchy Questions
- ![[Pasted image 20220623004452.png]]
#### Page Placement
- The miss penalty for VM involves accessing the storage device making it quiet high
	- This means lowering miss rate becomes important
	- Designers offer fully associative placement to achieve this
		- Pages can be placed anywhere
- Consistent with reducing page faults, most OS use LRU for block replacement
- Most processors keep a use/reference bit
	- Set when a page is referenced
	- OS records these bits and uses them to determine the least recently accessed page
#### What happens on a Write
- VM always writes backl
- Write through would involve writing to storage each time making writes too expensive
### How is a Page Found
- Processor keeps a page table that contains the physical address of the block in memory
- Page table is indexed by the page/segment number
- The virtual address contains the page table index and the offset for the data in memory
- A translation look aside buffer is used to speed up address translation times
- ![[Pasted image 20220623004848.png]]
#### Fast Address Translation
- Page tables are usually so large they are kept in main memory
	- Every memory access requires two accesses to main memory:
		- To obtain physical address
		- To obtain the data
- By keeping address translations in a special cache this reduces the accesses required
	- Based off the idea of locality; if the data has locality then most likely so do the addresses
	- Special cache is referred to as a Translation Look aside Buffer (TLB)
- A TLB entry is simialr to a cache entry
	- Tag holds portions of the virtual address 
	- Data portion holds:
		- Physical page frame number
		- Protection field
		- Valid bit
		- Use bit
		- Dirty bit
- ![[Pasted image 20220623005305.png]]
- 