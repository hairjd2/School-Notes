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
# Network Technologies
---
- Method a network interface uses to access the medium and send data frames, and the structure of these frames
- Sometimes defines frame format and which media types can be used to transfer frames
## Network Technologies and Media
---
### Unshielded Twisted Pair (UTP)
---
- Most command media type in LANs
- Four pairs of copper wire with each pair tightly twisted together and contained in a plastic sheath or jacket
- The higher the cat #, the higher the cable's bandwidth potential
- Susceptible to electrical interference, which can cause data corruption
### Fiber-optic Cabling
---
- Typically used in large internetworks to connect switches and routers
- Good for carrying data at long distances and at high data rates
- Isn't susceptible to electrical interference
- Need two strands of fiber, one for tx and one for rx
### Coaxial Cable
---
- Obsolete as a LAN medium, but still used as the network medium for internet access via cable modem
- Og medium used by ethernet in physical bus topologies
- Limitied to 10 Mbps half-duplex comms
### Baseband and Broadband Signaling
---
- Network tech can used media in two main ways: broadband and baseband
- Baseband tx method sends digital signals in which each bit of data is represented by a pulse of electricity or light
- Broadband use analog techniques to encode binary 1s and 0s across a continuous range of values
## Ethernet Networks
---
- Most popular LAN technology
- Advantages:
	- Ease of installation
	- Sacalability
	- Media suppoirt
	- Low cost
	- Supports broad range of transmission from 10 Mbps to 10 Gbps
### Ethernet Addressing
---
- Every ethernet station must have a physical or MAC address
- When a frame is sent to the network medium, it must contain both source and destination MAC addresses
- If the destination address is the broadcast MAC address where its all Fs, the NIC reads the frame and sends it to the network protocol for further processing
### Ethernet Frames
---
- Ethernet networks can accamodate frames between 64 bytes and 1518 bytes
- A 14-byte frame header composed of these three fields
	- 6-byte destination
	- 6-byte source 
	- 2-byte type field
- Data field from 46 to 1500 bytes
- A frame trailer (FCS) of 4 bytes
- ![[Pasted image 20240225231902.png]]
- Exceptions to the 1518 max size
### Ethernet Media Access
---
- NIC must adhere to some rules governing how and when the medium can be access for tx before it does
- These rules are called its media access method or media access control
- In half-duplex, ethernet uses ==Carrier Sense Multiple Access with Collision Detection (CSMA/CD)==
- "Carrier sense" means to listen, so it waits to listen to see if the channel is busy
- It can have multiple computers and has collision detection
### Collisions and Collision Domains
---
- The extent to which signals in an ethernet bus topology network are propagated is called a collision domain
- ![[Pasted image 20240225233816.png]]
- All devices in a collision domain are subject to the possibility of a collision
- The more computers there are, the most likely a collision is to occur
- Usually associated with hubs, can happen with a computer connected to a switch, but can only happen if the NIC connected to the switch port is in half-duplex mode
### Ethernet Error Handling
---
- Its low cost and scalability is because its simple
- Considered a best-effort delivery system
- This is because it relies on network protocols to ensure reliable delivery of data
- Can also detect whether a frame has been damaged in transit
- It uses CRC
## Ethernet Standards
---
- Generally expressed in the IEEE number or the XBaseY term
- 10BaseT Ethernet or IEEE 802.3i
	- Runs over cat 3 or higher UTP cabling
- 10BaseTX Ethernet or IEEE 802.3u
	- Most common ethernet variety
	- Runs over cat 5e or higher UTP
	- Sometimes called "Fast Ethernet"
- 100BaseFX
	- Used as a backbone cabling
	- The F refers to it being fiber-optic
- 1000BaseT Ethernet or IEEE 802.3ab
	- Supports 1000 Mbps
	- Works over cat 5e or higher UTP cable
	- Does not dedicate wire pair to transmitting or receiving
- 2.5GBaseT and 5GBaseT or 802.3bz
	- Runs over cat 5e/6 cabling
- 10GBaseT Ethernet or IEEE 802.3an
	- Runs over four pairs of cat 6A or Cat 7 UTP cabling
# 802.11 Wi-Fi
