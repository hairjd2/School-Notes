# Memory 2
## Memory Address Decoding
- A processor can usually address a memory space that is much larger than the memory space that is *much larger* than the memory space covered by an individual memory chip. (Most of today's processors support a 64 bit bus - how big is that memory space?)
- ### The 3-to-8 Line Decoder
	- ![[Pasted image 20220309180537.png]]
	- Note that all *three* Enables (G2A, G2B, G1) must be active, e.g. low, low and high, respectively
	- Each output of the decoder can be attached to an 2764 EPROM (8Kx8)
	- 