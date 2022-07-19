# Class 1 (Review)
## Number Systems
- smallest size grabbable is a byte, not by bits
- In Intel assembly:
	- a word is 2B
	- double word is 4B
	- quad word is 8B
- For converting from decimal to binary for the fraction part, multiply by 2
- When adding a positive and negative number in two's complement, you must remove the extra bit
- Overflow can be detected when carry in and carry out don't match
## IEEE Floating Point Formats
- Typically deal with 32 bit and 64 bit formats
- IEEE floating point numbers are stored as follows:
	- Single format (32bits) has:
		- 1 bit for sign, 8 bits for exponent and 23 bits for fraction
		- bias is 127
	- Double format (64 bits) has:
		- 1 bit for sign, 11 bits for exponent and 52 bits for fraction
		- bias is 1023
### Examples
- 4.75 decimal to floating point
	- convert to binary: 100.11
	- Move it to the left to get  1.0011 x 2^+2
	- sign is 0
	- exponent is 2 + 127 = 129 = 10000001
	- fraction part would be {0011} + trailing 0's {0000000000000000000}
-  Equation to go the other way is $(-1)^s*(1+m)*2^e$
	- s is the value of the sign bit
	- m is the mantisa
	- e is the exponent
## Digital Logic Review
- Logic gates:
	- AND
	- OR
	- Inverter
	- XOR
### Decoders
- Logic gates used to decode n input to 2^n output
	- Each output goes high iff the input matches that particular output
	- Decoders test for each possible minterm
	- Make it easy to transfer a truth table to circuit
- Can model with a truth table and design it
- Since it includes all outcomes, if not all used then its a waste of added internal circuitry
### Multiplexor (MUX)
- Mux is another common component that can be built using logic gates
- Mux contains one output, n select signals and $2^n$ inputs
	- The output copies an input 
- Disadvantage is similar to Decoder
## Sequential Logic
- Feedback allows memory to be stored within gates by feeding the output back into the input
- Types of latches:
	- SR (Set and Reset)
		- ![[Pasted image 20220529200312.png]]
	- JK
	- D (Data)
		- ![[Pasted image 20220529200323.png]]
		- Set D to 1 when want to switch state
		- E (enable) set to active low to enable switching
		- Can feed clk into E
	- T
### Flip Flops
- Can use D latches to build memory elements with better predictability
- Known as D flip flops
-  Built with two D latches with enables inverted
-  Data only changes on rising edge of enable signal
- Flip flop is 1 bit register
- ![[Pasted image 20220529201319.png]]
### Clock
- To offer even better predictability the enable signal of a DFF is usually tied to a clock signal
-  A clock signal has a set frequency and period 
	- This means that we can predict when the rising edge of the clock will come 
	- Thus we can set up the data to be saved in time
- Clocks are an important aspect of digital logic design 
	- Any design with sequential logic (memory) in it needs a clock 
	- Clock is used to synchronize all memory elements of the circuit 
	- Designs try to synchronize the circuit to one clock 
		- Multiple clocks in one design makes it hard to ensure you read the expected data
## Flip Flops and Registers
- ![[Pasted image 20220529203042.png]]
- To make a multi bit register, you add flip flops in parallel
- Each flip flop represents a bit in the register