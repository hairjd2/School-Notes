# Class 2 (Arithmetic Circuits)
- Can design combinationally and bottom up:
	- Adder
	- Multiplier
	- Divider
	- ALU
## Adders
- Takes two binary numbers and adds them producing a sum and cout
- Built using XOR and AND 
- Full adder:
	- ![[Pasted image 20220531181603.png]]
	- Summation can be found using xor
	- a and b can be used for cout
	- Sum = A xor B xor Cin
	- Cout AB or ACin or BCin
### Carry Look Ahead Adder (Propogate and Generate)
- ![[Pasted image 20220531182333.png]]
	- $Cin_(i+1)=G_i+C_iP_i$
	- Less reliance on the ripple
	- Pay attention to Carry look ahead adder
### RCA vs. CLA
- RCA carry is rippled through
	- As more bits are added, the propagation delay for the carry increases
	- Easier to build and does not require as much hardware 
- CLA carry is generated at each stage 
	- As more bits are added, the more complicated it gets 
	- Less propagation delay but more complicated to build § Typically restricted to 4 bits and then have the 4 bit components combined
## Multipliers
- Multiplies two binary numbers
- Product will be double the number of bits of the original numbers
- Typically very expensive
- Focus on that uses adders and shifts
- Can brute force every single product bit, but gets extremely complicated after awhile
### Multiplier Algorithms
- Better method is to use shift then add instead of brute force combinational logic
- ![[Pasted image 20220531212309.png]]
- ![[Pasted image 20220531212315.png]]
- ![[Pasted image 20220531212616.png]]
- How do we improve this:
	- Use multiplicand that's the same as the multiplier so that you don't waste bits
	- Lets you use a smaller adder, which means that there is less ripple
### Improved Algorithm 2.0
- ![[Pasted image 20220531212852.png]]
- ### Improved Algorithm 3.0
	- ![[Pasted image 20220531214000.png]]
## Booth's Algorithm
- For signed multiplication, you can apply normal multiplication, then add the sign later
	- This does not work every time
- Booth's algorithm is for multiplying signed numbers
- Reduces the number of adds that need to be done
- Follows the following steps
	1. Compare the current product's lsb and its previous
		- If they are 00: no arithmetic operation
		- If they are 01: add the multiplicand to the left half of the product
		- If they are 10: subtract multiplicand from left half of the product
		- If they are 11: no arithmetic operation
	2. Shift the product register to the right for 1 bit
		- Remember to maintain the current sign as you shift
- ![[Pasted image 20220602190028.png]]
## Division
- Implementation is so bad that alot of processors don't even include them
- Dividing two n bit numbers needs n+1 steps
- ![[Pasted image 20220602193622.png]]
- ![[Pasted image 20220602193817.png]]
### Algorithm 2.0 
- In the first version:
	- half the divisor is 0
	- We can also use a smaller adder/subtractor
- New algorithm:
	- Uses an n bit divisor and quotient (not 2n)
	- N bit adder/subtractor
	- 2n remainder register
- You need to shift the remainder to right
	- Do not shift the divisor
- Switch first step to shift first then subtract
	- Saves an iteration
- ![[Pasted image 20220602194302.png]]
- ![[Pasted image 20220602194249.png]]
### Algorithm 3.0
- We can improve on this further by combining the quotient and remainder register
- New registers become:
	- N bit divisor register
	- 2n bit register for
		- Remainder (MSB)
		- Quotient (LSB)
- ![[Pasted image 20220602194621.png]]
#### Can combine multiplication and division logic
- ![[Pasted image 20220602200110.png]]
### Dividing Signed Numbers
- Simplest approach is to remember signs, make positive, and complement quotient and remainder if necessary
## Floating Point Arithmetic
- IN FPA exponents must be handled as well as the magnitudes of the operands.
- The exponents of the operands must be made equal for addition and subtraction
		- The fractions are then added or subtracted as appropriate, and the result is normalized
- Example: Perform the following addition: (.101 x 2^3 + .111 x 2^4)_2
	- Must make both be the higher exponent
	- Add the magnitudes
- ![[Pasted image 20220602202250.png]]
### FP Multiplication and Division
- Similar to add/sub, except that the sign, exponent and fraction of the result can be computed separately
- Like/unlike signs produce +/- results, respectively
- Exponent of result is obtained by add/sub exponents
- Fractions are multiplied or divided according to the operation, and then normalized
## ALU 
- ALU is a multi-function higher level combinational logic unit whose operation can be changed by selecting one of several output functions
	- Functions can be arithmetic, logical or they can pass values to the output
	- The functions to be carried out are selected using an opcode
- Functionally an ALU is equivalent to multiplexed combinational building blocks
- It is a key component in processors as it handles a lot of the arithmetic functionality