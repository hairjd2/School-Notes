- “An action that prevents or impairs the authorized use of networks, systems, or applications by exhausting resources such as central processing units (CPU), memory, bandwidth, and disk space.”
- The Availability "pillar" is attacked
- A form of attack on the **availability** of some service
- Categories of resources that could be attacked are: ![[Pasted image 20230619160759.png]]
- ![[Pasted image 20230619160816.png]]
# Classic DoS Attacks
## Flooding ping command
- Aim of this attack is to **overwhelm the capacity of the network connection to the target organization**
- Traffic can be handled by higher capacity links on the path, but packets are discarded as capacity decreases
- **Source of the attack is clearly identified** unless a spoofed address is used
- Network performance is noticeably affected
## Source Address Spoofing
- Use forged source addresses
	- Usually via the raw socket interface on OS
	- Makes attacking systems hard to identify
- Attacker generates large volumes of packets that have the target system as the dest address
- Congestion would result in the router connected 
- Requires network engineers to specifically query flow info from their routers
- Backscatter traffic
	- Advertise routes to unused IP addresses to monitor attack traffic
## SYN Spoofing
- Attacks the ability of a server to respond to future connection requests by overflowing the tables used to manage them
- Thus legitimate users are denied access to the server
- Hence on attack on system resources, specifically the network handling code in the OS
- ![[Pasted image 20230707190211.png]]
- ![[Pasted image 20230707190252.png]]
## Flooding Attacks
- Classified based on network protocol used
- ==Intent is to overload the network capacity on some link to a server==
- Virtually any type of network packet can be used
- ![[Pasted image 20230707190405.png]]
# Distributed Denial of Service (DDoS)
- ![[Pasted image 20230707190521.png]]
- ![[Pasted image 20230707190532.png]]
- ![[Pasted image 20230707190542.png]]
# Hypertext Transfer Protocol (HTTP) Based Attacks
- ![[Pasted image 20230707190701.png]]
# Reflection Attacks
- ![[Pasted image 20230707190716.png]]
- ![[Pasted image 20230707190800.png]]
# DNS Amplification Attacks
- ![[Pasted image 20230707190810.png]]
- ![[Pasted image 20230707190847.png]]
# DOS Defense and Prevention
## Defense
- These attacks ==cannot be prevented entirely==
- High traffic volumes may be legitimate
	- High publicity about a specific site
	- Activity on a very popular site
	- Described as **slashdotted, flash crowd, or flash event** e.g. Olympics or World Cup
- ![[Pasted image 20230707191016.png]]
## Prevention
- Block spoofed source addresses
	- On routers as close to source as possible, e.g., before leaving ISP network
- Filters may be used to ensure path back to the claimed source address is the one being used by the current packet
	- Filters must be applied to traffic before it leaves the ISP's network or at the point of entry to their network
- Use modified TCP connection handling code
	- Cryptographically encode critical info in a cookie that is sent as the server's initial sequence number
		- Legitimate client responds with an ACK packet containing the incremented sequence number cookie
	- Drop an entry for an incomplete connection from the TCP connections table when it overflows
- Block IP directed broadcasts
- Block suspicious services and combos
- Manage application attacks with a form of graphical puzzle (captcha) to distinguish legitimate human requests
- Good general system security practices
- Use mirrored and replicated servers when high-performance and reliability is required
## Responding to DoS attacks
- ![[Pasted image 20230707191504.png]]
- ![[Pasted image 20230707191525.png]]