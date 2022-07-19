# Class 11: Buses
## Bus Architecture
- The connection between the IO devices, processor, and memory are usually called (local or internal) buses
- Communication among the devices and the processor use both bus protocols and interrupts
- A bus is a shared communication link which uses one set of wires to connect multiple subsystems
- The two major advantages of the bus organization are:
	- Versatility: adding new devices and moving current ones among computers
	- Low cost: single set of wires are shared in multiple ways
- The major disadvantage of a bus is that it creates a communication bottleneck possibly limiting throughput
- The max bus speed is largely limited by physical factors: the length of the bus and the number of devices
- Increasing bus bandwidth (throughput) can be achieved using buffering which slow down bus access (response time)
- A bus protocol is enforced to define the semantics of the bus transaction and arbitrate bus usage
### System Bus
- Original design had one system bus connecting the entire system
- This was divided into:
	- Control bus
	- Bidirectional
	- Control signals
- Address bus
	- Unidirectional
	- For address signals
- Data bus
	- Bidirectional
	- Data signals
- ![[Pasted image 20220703172923.png]]
### Types of Buses
- Processor-memory (local) bus:
	- Generally short and high speed to maximize the bandwidth
- I/O Bus 
	- Lengthy and supportive to multiple data rates and devices
	- Do not interface directly to memory but use local or backplane bus 
	- Must handle wide range of device latency, bandwidth and characteristics
- Backplane Bus
	- Received that name because they lay in the back of the chassis structure
	- Allows memory, processor and I/O devices to be connected
	- Requires additional logic to interface to local and I/O buses
- Local buses may be design-specific while IO and backplane buses are usually portable and often follow industry-recognized standard
- A system can use one backplane or a combination of multiple buses to link memory, processor and the various IO devices.
### Bus Configurations
![[Pasted image 20220706001801.png]]
### Synchronous vs. Asynchronous Bus
- Sync bus:
	- Clock based protocol and time-based control lines
	- Simple interface logic and fast bus operations
	- Every device on the bus must run at the same clock rate
	- Because clock skew, sync buses cannot be long
	- Local buses are often sync
- Async Bus:
	- Not clock-based -> can accommodate a wide variety of devices
	- Not limited in length because of clock skew
	- Uses a handshaking protocol to ensure coordination among communicating parties
	- Requires additional control lines and logic to manage bus transactions
## Bus Performance
- ![[Pasted image 20220706002652.png]]
### Increasing bandwidth
- Much of bus bandwidth is decided by the protocol and timing characteristics
- The following are other factors for increasing the bandwidth:
	- Data bus width:
		- Transfers of multiple words requires fewer bus cycles
		- Increases the number of bus lines
	- Multiplexing address and data line:
		- Uses separate lines for data and address, speeds up transactions
		- SImplifies the bus control logic
		- Increases the number of bus lines
	- Block transfer:
		- Transfers multiple words in back-to-back bus cycles without releasing the bus or sending new address
		- Increases response time since transactions will be longer
		- Increases complexity of the bus control logic
- Increasing the number of bus lines has very significant impact on the bus cost
## Bus Access
- IO should occur without processor's continuous and low-level involvement
- A bus master, e.g., processor, controls access to the buys and initiates and manages bus requests
- A bus slave, e.g. memory, only responds to access requests but never initiate its own requests
- A single bus master is very simple to implement but requires the involvement of the processor in every transaction
- Multi-master buses requires abritration to coordinate bus usage among potential access requesters
### Bus arbitration
- Bus arbitration coordinates bus usage among multiple devices using request, grant, release mechanism
- Arbitration usually tries to balance two factors in picking the granted device:
	- Devices with high bus-priority should be served first
	- Maintaining fairness to ensure that no device will be locked out from the bus
- Arbitration time is an overhead
	- Should be minimized to expedite bus access
#### Arbitration Schemes
- Distributed arbitration by self-selection: (e.g. NuBus used by Apple Macintosh)
	- Uses multiple request lines for devices
	- Devices requesting the bus determine who will be granted access
	- Devices associate a code with their request indicating their priority
	- Low priority devices leave the bus if they notice a high priority requestor
- Distributed arbitration by collision detection: (e.g. Ethernet)
	- Devices independently request the bus and assume access
	- Simultaneous requests result in a collision
	- A scheme for selecting among colliding parties is used
- Daisy chain arbitration: (e.g. VME bus)
	- The bus grant line runs through devices from highest priority to lowest
	- High priority devices simply intercept the grant signal and prevent the low priority device from seeing the signal
	- Simple to implement (use edge triggered bus granting)
	- Low priority devices can starve (grant signals take long to reafch the last device in the chain)
	- Allow fault propagation (failure of a high priority device might lock the bus)
- Centralized, parallel arbitration: (e.g. PCI bus)
	- Uses multiple request-lines and devices independently request bus (one line / device)
	- A centralized arbiter selects a device and notifies it to be the bus master
	- The arbiter can be a bottleneck for bus usage
### Bus Standards
- IO bus serves as a way of expanding the machine and connecting new peripherals
- Standardizing the bus specifications ensure compatibility and portability of perpherals among different computers
- Popularity of a machine can make its IO bus a de facto standard, e.g. IBM PC-AT bus
- Examples of widely known bus standards are Small Computer Systems Interface (SCSI), Ethernet, and Peripheral Computer Interface (PCI)
- ![[Pasted image 20220706004612.png]]