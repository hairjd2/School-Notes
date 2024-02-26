# Physical Topologies
---
- Two different types of topologies
	- Physical topology: arrangement of cabling and how cables connect one device to another
	- Logical topology: Path that data travels between computers
## Physical Bus Topology
---
- Puts computers on single line (daisy-chain fashion)
- Limit of 30 computers per cable segment
- Max total length of cabling is 185 meters
- Both ends of the bus must be terminated
- Any break brings network down
- Adding or removing a machine brings down the network temporarily
- Limited to 10 Mbps half-duplex bc use of coax
- Need to install terminator to avoid
## Physical Star Topology
---
- Uses central device
- Must faster technology used compared to bus
- Centralized monitoring
- Network upgrades are easier
### Extended star topology:
---
- A star of star topologies
- Also called hierarchical star
- ![[Pasted image 20240225185521.png]]
- 
### Disadvantages:
---
- Central device represents single point of failure
- Needs more cables than bus, but the cable cost does not outweigh star's advantages over bus
## Physical Ring Topology
- Like bus where devices daisy-chained 
- Used to connect LANs to each other with a technology called Fiber Distributed Data Interface (FDDI)
- FDDI most often used as a reliable and fast network backbone, which is cabling sed to communicate between LANs or between switches
- ![[Pasted image 20240225191315.png]]
- Data travels in one direction, which means that if anything fails, data can no long be passed
- Tech like FDDI overcome problems with physical ring network by creating a dual ring, in which data can travel in both directions so that a single device failure doesn't break the entire
- This is costly though and physical rings have mostly been supplanted by extended star Ethernet installations
## Point-to-Point Topology
---
- Direct link between two devices
- Most often used in WANs
- Device on a business' network has a dedicated link to a telecommunication provider, such as the local phone company
- The connection then hooks into the phone company's network to provide internet access or a WAN or MAN link to a branch office
- Advantage is that data travels on a dedicated link, and its bandwidth isn't shared with other networks
- Tends to be expensive though, particularly when used as a WAN link to a distant branch office
- Also used with wireless networks in what is called a ==wireless bridge==
- Rudimentary LAN can also be setup with a point-to-point topology by connecting a cable between the NICs on two computers
### Point-to-Multipoint Topology (PMP)
- Arrangement where a central device communicates with two or more other devices and all communication goes through the central device
- Used in WANs where a main office has connections to several branch offices via a router
- Instead of the router having a separate connection each branch office, a single connection is made from the router to a switching device which then directs traffic to the correct branch office.
- Usually a cloud
### Mesh Topology
- Connects each device to every other device in a network
- Like multiple point-to-point connections for the purposes of redundancy and fault tolerance
- ![[Pasted image 20240225194348.png]]
- Although reliable, are expensive because of the additional cabling and ports required
- In most cases, the ports used to connect devices are the highest speed available, such a 1 Gbps or 10 Gbps, and often use fiber-optic cables
# Logical Topologies
- Describes how data travels from computer to computer
- In some cases, as with a physical bus and ring, the logical topology mimics the physical arrangement of cables
- In other cases, as with physical star, the electronics in the central device determine the logical topology
- A network's logical topology reflects the underlying network technology used to transfer frames from one device to another
- ![[Pasted image 20240225200137.png]]
- 