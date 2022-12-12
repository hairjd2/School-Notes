# File-System Structure
- File structure
	- Logical storage unit
	- Collection of related info
- **File system** resides on secondary storage (disks)
	- Provided user interface to storage, mapping logical to physical
	- Provides efficient and convenient access to disk by allowing data to be stored, located retreived easily
- **File control block** (FCB) - storage structure consisting information about a file
- **Device driver** controls the physical device
## File System Layers
- **Device drivers** manage I/O devices at the I/O control layer
	- Given commands like "read drive1, cylinder 72, track 2, sector 10, into memory location 1060" outputs low-level hardware specific commands to hardware controller
- **Basic file system** given commnd like "retreive block 123" translates to device driver
- **File organization module** understands files, logical address, and physical blocks
- **Logical file system** manages metadata information
	- Translates file name into file number, file handle, location by maintaining file control blocks (**inodes** in UNIX)
	- Directory management
	- Protection
- Layering useful for reducing complexity and redundancy, but adds overhead and can decrease
- Many fs', sometimes many within an OS
	- Each with its own format (CD-ROM is ISO 9660; UNIX has UFS, FFS; Windows FAT, FAT32, NFS, as well as floppy)
	- New ones still arriving - ZFS, GoogleFS, Oracle ASM, FUSE
# File-System Operations
- We have sys calls at the API level, but how to implement?
- **Boot control block** contains info needed by system to boot OS from that volume
- **Volume control block (superblock, master file table)** contains volume details
	- Total # of blocks, # of free blocks, block size, free block pointers or array
- Per-file **File Control Block (FCB)** contains many details about the file
	- Typically inode number, permissions, size, dates
	- NTFS stores into in master file table using relational DB structures
## In-Memory File System Structures
- **Mount table** storing file system mounts, mount points, file system types
- **System-wide open-file table** contains a copy of the FCB of each file and other info
- **Per-process open-file table** contains pointers to appropriate entries in system-wide open-file table as well as otherr info
- ![[Pasted image 20221212102713.png]]
# Directory Implementation
- **Linear List** of file names with pointer to the data blocks
	- Very common, and simple to program
	- Time-consuming to execute
- **Hash Table** - Linear list with hash data structure
	- Decreases directory search time
	- **Collisions** - situations where two file names hash to the same location
# Allocation Methods
## Contiguous
- An allocation method refers to how disk blocks are allocated for files:
- **Contiguous allocation** - each file occupies set of contiguous blocks
	- Best performance in most cases
	- Simple - only starting location (block #) and length (number of blocks) are required
	- Great for things like CD-ROM
	- Only works well for ROM
### Extent-Based Systems
- Many newer file systems (i.e. Veritas File System) use a modified contiguous allocation scheme
- Allocate disk blocks in extents
- An **extent** is a contiguous block of disks
- Veritas is not that important - a thing that exists
## Linked
- **Linked Allocation** each file a linked list of blocks
	- File ends at null pointer
	- No external fragmentation, but will have internal fragmentation
	- Great for sequential access, but not for random access
	- Can improve efficiency through clustering, but increases internal fragmentation
	- Bad for reliability, because if a node is corrupted, the rest of the list is lost
- FAT (File Allocation Table) variation
	- Beginning of volume has table, indexed by block number
	- Much like a linked list, but faster on disk and cacheable
	- New block allocation simple
	- ![[Pasted image 20221212103704.png]]
## Indexed
- **Indexed allocation**
	- Each file has its own **index block(s)** of pointers to its data blocks
- Logical view
	- ![[Pasted image 20221212103804.png]]
- ![[Pasted image 20221212103821.png]]
## Performance
- Best method depends on file access type
	- Contiguous great for sequential and random
- Linked good for sequential, not random
- Declare access type at creation -> either contiguous or linked
- Indexed more complex
	- Single block access could require 2 index block reads then data block read
	- Clustering can help improve throughput, reduce CPU overhead
- For NVM, no disk head so different algorithms and optimizations needed
- Its alright if more complicated since the performance of the CPU will exponentially out perform memory IO
# Free-space management
- FS maintains **free-space list** to track available blocks/clusters
	- (Using term "block" for simplicity)
- **Bit vector** or **bit map** (*n* blocks)
- Bit map requires extra space
- Easy to get contiguous files
- Grouping
	- Modify linked list to store address of next n-1 free blocks in first free block, plus a pointer to next block that contains free-block-pointers (like this one)
- Counting
	- Becaues space is frequently contiguously used and freed, with contiguous-allocation, extents, or clustering
		- Keep address of first free block and count of following free blocks
		- Free space list then has entries containing addresses and counts
## TRIMing Unused Blocks
- A way for the drive to clean up blocks when its more convenient
- Lets the drive overwrite stuff when it needs to
# Efficiency and Performance
- Can make things faster when you cache things
- Things will be done asynch when possible
- Synch has to be done for read, write can be asynch
## Page Cache
- Treat the blocks of the disk as pages, and do page in and out the same as you do for swap
- Can do this with a unified or ununified buffer cache
# Recovery
- FS can be corrupted, will have fail systems
- Will constantly check to see if you're in a safe state, if not it will run recovery methods
- May lose data from this
## Log Structured FS
- **Log structured (or journaling)** fs' record each metadata update to the fs as a transaction
- All transactions are written to a log