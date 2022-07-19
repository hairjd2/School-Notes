# Class 2: Basics - Review
- Know how to do binary
- Each F=4 bits
	- A leading 0x1 adds 1 bit
	- A leading 0x3 adds 2 bits
	- A leading 0x7 adds 3 bits
	- A leading 0xF adds 4 bits
	- Each following F adds 4 bits (3 Fs = 12 bits)
- ![[images/Pasted image 20220202174207.png]]
## Basic Architecture
### Bus
- Simply defined as a "group of wires"
- The 0x# address defines where the data is in the bus
- ==Common bits==
	- Nibble is 4 bits
	- Byte is 8 bits
	- 10 bits is kilobit
	- 20 bits is Mb
	- 30 bits is Gb
	- 40 bits is Terrabit
	- 50 bits is Petabit
#### Parallel Bus
- ==Parallel Interfaces== transfer multiple bits at the same time. They usually require buses of data - transmitting across eight, sixteen, or more wires. Data is transferred in huge, crashing waves of 1's and 0's
#### Serial Bus
- ==Serial Interfaces== stream their data, one single bit at a time. These interfaces can operate on as little as one wire, usually never more than four. 
#### Types of buses
##### - Data Bus
##### - Address Bus
- If I/O, a value between 0000H and FFFFH is issued
- If memory, it depends on the architecture:
	- 20-bits (8086/8088)
	- 24 bits
- Send the address to memory, then the data for writing
- Send the address to memory for 
##### - Control Bus
- Most Intel systems have at leasat 4 control bust connections
#### Practice problem
![[images/Pasted image 20220202182506.png]]
##### - Example 1
- Address 
##### - Example 2
- Address bus width: 13
- Data bus width: 2 bytes
- Data bus width: 16 bits
- Memory size: 8192 bits
##### - Example 3
- Address bus width: 14 (16384 bytes)
## Two's complement
- Found by adding 1 to the LSB of the 1's complement
- The negative number of something means the two's complement
## Error Detection
- Can use the parity bit to determine errors
### SECDED Fundamental Definitions
- Weight: the number of 1's in the data
	- Example: W(1011101) = 5
- Distance: The Hamming distance between two words (of equal length) is the number of bit positions in which they differ. It is the pop count of the exclusive or of the two words
	- Example: HD(1011101, 1011010) = 3
- Even parity: The amount needed to add in order to make it even
- Opposite for odd parity
- This can only detect a single bit error
### Block-check character (BCC) or Checksum
- Can detect multiple bit errors.
- This is simply the ==two's complement sum== (the negative of the sum) of the sequence of bytes
- No error occurred if adding the data values and the checksum produces a 0.
- Not fool proof, if there are multiple errors that lead to the same sum
### Cyclic Redundancy Check (CRC)
- Commonly used to check data transfers in hardware such as hard drives.
- Treats data as a stream of serial data n-bits long
	- The bits are treated as coefficients of a ==_characteristic polynomial_==, M(X) of the form:
- Where b<sub>o</sub> is the LSB while b<sub>n</sub> is the MSB
- ![[Pasted image 20220207181446.png]]
- Most used CRC polynomials:
	- CRC-12
	- CRC-16
	- CRC-CCITT
	- CRC-32
- The CRC is found by applying:
	- ![[Pasted image 20220207181608.png]]
- G(X) is called the ==_generator polynomial_== and has special properties
- The remainder R(X) is appended to the data block.
- When the CRC and R(X) is computed by the receiver, R(X) should be zero.
- The length of the CRC field is the max power of the polynomial
- To first generate the CRC, send in the signal with the CRC field set to all zeroes.
- Once the signal has propogated all the way to the end, the remaining three bits are the CRC check that will be used to verify the signal for the receiving end.
- This CRC check can then be used by the receiving end to make sure it has received the correct signal