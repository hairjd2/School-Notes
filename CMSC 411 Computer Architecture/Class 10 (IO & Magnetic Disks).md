# Class 10: IO/Magnetic Disks
## Input/Output (I/O)
- A system that facilitates communication between a host system and external devices
- System usually include:
	- Blocks of main memory dedicated to IO functions
	- Buses that move data around
	- Control modules in host and external devicesw
	- Interfaces to external components such as keyboards
	- Communication links between host and peripherals
### Architecture
- Things to consider:
	- IO interface:
		- Device drivers
		- Device controller
		- Service queues
		- Interrupt handling
	- Design Issues:
		- Performance
		- Expandability
		- Standardization
		- Resilience to failure
	- Impact on Tasks:
		- Blocking conditions
		- Priority inversion
		- Access ordering
- IO can be controlled in the following general ways
	- Programmed IO:
		- Reserves a register for each device
		- Each registers is continually polled for data arrived
	- Interrupt driven IO
	- Memory Mapped IO
		- Shares memory address space between IO and program memory
	- Direct Memory Access
		- Off loads IO to a special chip that handles the specifics
	- Channel IO
		- Uses dedicated IO processors
#### Memory Mapped IO
- IO and main memory share address space
	- Each device has its own reserved block of memory
	- From the CPU point of view IO access looks like memory access
	- Typically can use the same instructions to move data in and out of memory and IO
	- In smaller systems the low-level details are offloaded to the IO controllers in the IO devices
#### Direct Memory Access (DMA) IO
- ![[Pasted image 20220624011657.png]]
#### Interrupt IO
- ![[Pasted image 20220624011725.png]]
### Performance
- ![[Pasted image 20220624011811.png]]
- ![[Pasted image 20220624011830.png]]
- IO system performance depends on many aspects of the system
	- CPU
	- Memory system:
		- Internal and external caches
		- Main Memory
	- The underlying interconnection (buses)
	- IO controller
	- IO device
	- Speed of IO software (OS)
	- Efficiency of the software's use of the IO devices
- Two common performance metrics
	- Throughput: IO bandwidth
	- Response time: latency
#### Producer-Server Model
- Throughput
	- The number of tasks completed by the server in unit time
	- In order to get the highest possible throughput:
		- The server should never be idle
		- The queue should never be empty
- Response time:
	- Begins when a task is placed in the queue
	- Ends when it is completed by the server
	- In order to minimize the response time:
		- The queue should be empty
		- The server will be idle
- ![[Pasted image 20220624012203.png]]
#### Throughput Enhancement
- In general throughput can be improved by:
	- Throwing more hardware at the problem
	- Reduces load-related latency
- Response time is much harder to reduce:
	- Ultimately it is limited by the mechanical subsystems
- ![[Pasted image 20220624012315.png]]
## (Magnetic) Disk Storage
- Purpose:
	- Long term, nonvolatile storage
	- Large, inexpensive, and slow
	- Low level in the memory hierarchy
- Two major types:
	- Floppy disk
	- Hard disk
- Both types of disks:
	- Rely on a rotating platter coated with a magnetic surface
	- Use a movable read/write head to access the disk
- Advantages of hard disks over floppy disks
	- Platters are more rigid (metal or glass) so they can be larger
	- Higher density because it can be controlled more precisely
	- Higher data rate because it spins faster
	- Can incorporate more than one platter
### Organization
- ![[Pasted image 20220624014237.png]]
- Typical numbers (depending on the disk size)
	- 500-2,000 tracks per surface
	- 32-128 per track
		- A sector is the smallest unit that can be read or written to
- Traditionally all tracks have the same number of sectors:
	- Constant bit density: record more sectors on the outer tracks
	- Recently relaxed: constant bit size, speed varies with track location
### Magnetic Disk Operation
- Cylinder: all the tracks under the head at a given point on all surface
- Read/write data is a three-stage process:
	- Seek time: position the arm over proper track
	- Rotational latency: wait for the desired sector to rotate under the read/write head
	- Transfer time: transfer a block of bits (sector) under the read-write head
- Average seek time
	- (Sum of the time for all possible seek) / (total # of possible seeks)
	- Typically in the range of 8ms to 12ms (as reported by the industry)
	- Due to locality of disk reference, actual average seek time may only be 25%-33% of the advertised number
### Magnetic Disk Characteristic
- Rotational Latency
	- Most disks rotate at a speed of 3600 to 7200 RPM
	- Approx. 16-8ms per revolution, respectively
	- An average latency to the desired information is halfway around the disk: 8m at 3600 RPM, 4ms at 7200 RPM
- Transfer Time is a function of:
	- Transfer size (usually a sector): 1 KB / sector
	- Rotational speed: 3600 RPM to 7200 RPM
	- Recording density: bits per inch on a track
	- Diameter: typical diameter ranges from 2.5 to 5.25 in 
	- Typical values: 2 to 12 MB per second
### Performance
- ![[Pasted image 20220624015013.png]]
- Disk Access Time = Seek time + rotation latency + transfer time + controller time + queuing delay
- Estimating Queue Length:
	- Utilization = U = Request Rate / Service Rate
	- Mean Queue Length = U / (1 - U)
- Never can have request rate == service rate
#### Example
- ![[Pasted image 20220624015247.png]]
- ![[Pasted image 20220624015308.png]]
#### I/O Benchmarks for Magnetic Disks
- Supercomputer application:
	- Large-scale scientific problems => large files
	- One large read and many small writes to snapshot computation
- Translation processing:
	- Examples: airline reservations systems and bank ATMs
	- Small changes to large shared databases
- File system:
	- Measurements of UNIX file systems in an engineering environment:
		- 80% of accesses are to files less than 10 KB
		- 90% of all file accesses are to data with sequential disk addresses
		- 67% of the accesses are reads, 27% writes, 6% read-write
### Reliability and Availability
- Two terms that are often confused:
	- Reliability: Is anything broken?
	- Availability: Is the system still available to the user?
- Availability can be improvd by adding hardware
- Reliability can only be improved by:
	- Enhancing environmental conditions
	- Building more reliable components
	- Building with fewer components
		- Improve availability may come at the cost of lower reliability
#### Disk Arrays
- A new organization of disk storage
	- Arrays of small and inexpensive disks
	- Increase potential throughput by having many disk drives:
		- Data is spread over multiple disks
		- Multiple accesses are made to several disks
- Redundant Array of Inexpensive Disks (RAID)
	- Widely available and used in today's market
	- Different levels based on the number of replicas
- Reliability is lower than a single disk:
	- But availability can be improved bay adding redundant disks (RAID): Lost information can be reconstructed from redundant information
	- MTTR: mean time to repair is in the order of hours
	- MTTF: mean time to failure of disks is tens of years