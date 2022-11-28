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
# NVM Scheduling
# Error Detection and Correction
# Storage Device Management
# Swap-Space Management
# Storage Attachment
# RAID Structure