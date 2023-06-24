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