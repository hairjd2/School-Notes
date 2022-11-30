# Overview of Mass Storage Structure
- Bulk of secondary storage for modern computers is **hard disk drives (HDD)** and **nonvolatile memory (NVM)** devices
- **HDDs** spin platters of magnetically-coated material under moving read-write heads
	- Drives rotate at 60 to 250 times per second
	- **Transfer rate** is rate at which data flow between drive and computer
	- **Positioning time (random-access time)** is time to move disk arm to desired cylinder (**seek time**) and time for desired sector to rotate under the disk head (**rotational latency**)
	- **Head crash** results from disk head making contact with the disk surface -- that's bad
- Disks can be removable
## HDD
- Platters range from .85" to 14"
- Range from 30GB to 3TB per drive
- Performance
	- Transfer rate - theoretical - 6 Gb/sec
	- Effective Transfer Rate - real - 1 Gb/sec
	- Seel time from 3ms to 12ms - 9ms common for desktop drives
	- Average seek time measured or calculated based on 1/3 of tracks
	- Latency based on spindle speed
		- 1/(RPM / 60) = 60 / RPM
	- Average latency = 1/2 latency
## Nonvolatile Memory Devices (NVM)
- If disk-drive like, then called SSD's
- Other forms include USB dribes, DRAM disk replacements, surface-mounted on motherboards, and main storage in devices like smartphones
- Can be more reliable than HDDs
- More expensive per MB
- Maybe have shorter life span - need careful management
- Less capacity
- But much faster
- Busses can be too slow -> connect directly to PCI for example
- No moving parts, so no seek time or rotational latency
- Have characteristics that present challenges
- Read and written in "page" increments (think sector) but can't overwrite in place
	- Must first be erased, and erases happen in larger "block" increments
	- Life span measured in **drive writes per day (DWPD)**
	- 
# HDD Scheduling
- The OS is responsible for using hardware efficiently - for the disk drives, this means having a fast access time and disk bandwidth
- Minimize seek time
- Seek time ~= seek distance
## SCAN
- The disk arm starts at one end of the disk, and moves toward the other end, servicing requests until it gets to the other end of the disk, where the head movement is reversed and servicing continues.
- **SCAN algorithm** somtimes called their **elevator algorithm**
- If requests are uniformly dense, largest density at other end of disk and those wait the longest
- ![[Pasted image 20221130102225.png]]
## C-SCAN
- Same as SCAN, but only goes in one direction
- More uniformity, but technically can move more
- ![[Pasted image 20221130102315.png]]
## Selecting a Disk-Scheduling Algorithm
- SSTF is common and has a natural appeal, but still inefficient
- SCAN and C-SCAN perform better especially when there is a heavy-load and make things more uniform
	- Less starvation but still possible
- To avoid starvation Linux implements **deadline** scheduler
	- Maintains separate read and write queues, gives read priority
		- Because processes more likely to block on read than write
	- Implements four queues: 2 x read and 2 x write
		- 1 of each is placed in sorted in LBA order, essentially implementing C-SCAN
		- 1 of each is sorted in FCFS order
- Linux will let the native command scheduler to do it itself
- Can say C-SCAN is the most common, or SCAN
- RHEL 7 also NOOP and completely fair queueing scheduler (CFQ)
# NVM Scheduling
- No physical movement, so NOOP is the order chosen (no scheduling)
- This is because you can move around willy nilly
	- NVM best at random I/O, HDD at sequential
	- **I/O operations per second (IOPS)** much higher with NVM (hundreds of thousands vs hundreds)
# Error Detection and Correction
- **Error detection** determines if there a problem has occurred determines if there a problem has occurred (for example a bit flipping)
- Parity one form of **checksum** - uses modular arithmetic to compute, store, compare values of fixed-length words
- Parity one form of **checksum** - uses modular arithmetic to compute, store, compare valeus of fixed-length words
	- Another error-detection method in networking is CRC
- **Error-correction code (ECC)** not only detects, but can correct some errors
- Erasure coding finds a way to split a file down a magical combo
# Storage Device Management
- **Low-level formatting**, or **physical formatting** - Dividing a disk into sectors that the disk controlelr can read and write
- To use a disk to hold files, the OS still needs to record its own data structures on the disk
	- **Partition** the disk into one or more groups of cylinders, each treated as a logical disk
	- **Logical formatting** or "making a file system"
	- To increase efficiency most file systems group blocks into clusters
- **Root partition** contains the OS, other partitions can hold other OSes, other file systems, or be raw
	- **Mounted** at boot time
- At mount time, file system consistency checked
- Boot block can point to boot volume or boot loader set of blocks that contain enough code to know how to load the kernel from the file system
# Swap-Space Management
- Used for moving entire processes (swapping), or pages (paging), from DRAM to secondary storage when DRAM not large enough for all processes
- OS provides swap-space management
# Storage Attachment
- Computers access storage in three ways
## 1. Host-attached
- Access through local I/O ports, using one of several technologies
	- To attach many devices, use storage busses such as USB, firewire, thunderbolt
	- High-end systems use **fibre channel (FC)**
## 2. Network-attached
- Network-attached storage (NAS) is storage made available over a network rather than over a local connection
- NFS and CIFS are common protocols
## 3. Cloud Storage
- Simialr to NAS, just over the internet
- NAS presented as just another file system, while cloud storage is API based
## Storage Array
- Can just attach disks, or arrays of disks
- Avoids the NAS drawback of using network bandwidth
# RAID Structure
- **RAID - redudant array of inexpensive disks**
- Multiple disk drives provides reliability via redudancy
- Increases mean time to failure
- Mean time to repair - exposure time when another failure could cause data loss
- Mean time to data loss based on things above
- Frequently combined with **NVRAM** to improve write performance
- ![[Pasted image 20221130110634.png]]
- ![[Pasted image 20221130110657.png]]
- ![[Pasted image 20221130110710.png]]
- 