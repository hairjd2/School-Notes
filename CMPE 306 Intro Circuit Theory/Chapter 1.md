# Syllabus
- Expected to read a chapter every week
- The labs will be done in pairs
- Students will have to write 4 of the lab reports as it is alternated with the partner
- Homeworks are graded on effort
- Don't come more than 10 minutes late
- Two midterms and one final
- Closed book, note, and formula sheet
- Can use a graphing calcualator (learn how to use matrices on it)
- Need an 86% for an A

Assignment | Grade Percentage
------------ | ------------
Homework | 10%
Weekly labs | 10%
Final lab | 10%
Midterm 1 | 15%
Midterm 2 | 20%
Final | 35%

# Chapter 1 Basic Concepts
## Electric Circuit Elements
- Resistor
- Capicitor
- Inductor
- Voltage Sources
- Current Sources
- Not covered
	- Operational amplifier
	- Diodes
	- Transistors
## Circuit Variables
### Current and Charge
- #### Charge: a physical property associated with certain fundamental particles and has polarities
	- electron: -e
	- proton: +e
	- neutron: 0
	- e = 1.6x10^-19 C
- #### Law of conservation of charge: charges can neither be created nor destructed, only be transported
- #### Current: the time rate of transporting charges across a cross section area
	- i = dq/dt
	- in Amps
	- Q = integral(i(t')dt') from 0 to t
	- Differential relation between charge and current
	- For i > 0
		- Positive charges flow in the reference direction
		- negative charges flow in the opposite direction
	- Opposite for i < 0
	- So when the amps are negative, the charges are flowing in the opposite direction
	- DC is constant in time
	- AC is sinusoidal
### Voltage
- How to make charges move
	- Under electric force
	- electric potential difference
- U: electric potential at a given point in a circuit
- Voltage is the electric potential difference ==between two points==
- ==Voltage has polarities==
	- "+" terminal: (reference) high potential point
	- "-" terminal: (reference) low potential point
- V = U^+ - U^-
	- + to - is a voltage drop
	- - to + is a voltage rise
- W = delta(q)U
- ==V = U^+ - U^- = dW/dq==
	- Electric energy ==loss== when unit positive charge (delta(q) = +1C) moving from + to - points
	- Electric energy ==gain== when unit positive charge moving from - to + points
### Power: the time rate of supplying or absorbing energy
- p = dW/dt (Work per unit of time)
- Differential relation between work and power
- p = vi
- p > 0: power is absorbed by the element
- p < 0: power is supplied by the element
- Law of conservation of energy (power): delta(p_absorbed) = delta(p_supplied)
## Circuit Elements
- ## Passive elements
	- Resistor
	- Capicitor
	- Inductor
- ## Sources (active circuit elements)
	-   | independent source (value specified | dependent source (dependence specified)
		-| ------------------------------------ | ---------------------------------------------
		Voltage source (v<sub>s</sub>(t) specified, i<sub>s</sub> to be determined) | ![[Pasted image 20220203101233.png]] v<sub>s</sub> value specified | ![[Pasted image 20220203101258.png]]v<sub>s</sub> = $\alpha$v<sub>x</sub> or v<sub>s</sub> = $\beta$i<sub>x</sub>
		Current source (i<sub>s</sub>(t) specified, v<sub>s</sub> to be determined) | ![[Pasted image 20220203101723.png]] i<sub>s</sub> value specified | ![[Pasted image 20220203101753.png]] i<sub>s</sub> = $\gamma$v<sub>x</sub> or i<sub>s</sub> = $\rho$i<sub>x</sub>
		

	- The subscript s stands for the source
	- v<sub>x</sub> or i<sub>x</sub> is the voltage or current at other location of the circuit. 
## Passive Sign Convention
- Sign used in an equation involving V and I associated with a two-terminal element based on the voltage polarity and current direction
- Make sure to get the sign down or value will be very wrong
- Use "+" sign in equation when: ![[Pasted image 20220203102318.png]]
- Use "-" sign in equation when: ![[Pasted image 20220203102356.png]]
- Charges losing energy means that the element is absorbing power, meaning that it must be positive
- Vice versa if the charge is gaining energy
### Example
- ![[Pasted image 20220203103512.png]]
- Dependent voltage source value
	- 0.6I<sub>x</sub> = 3V, V<sub>3</sub> = V<sub>4</sub> = 3V
	- V<sub>1</sub> = 2 + 3 = 5V
	- I<sub>3</sub> = 9 - 5 = 4A
- Power
- p<sub>1</sub> = -5V x 9A = -45W (supply)
- p<sub>2</sub> = 2V x 9A = 18W (absorb (under charging))
- p<sub>3</sub> = +3V x 4A = 12W (absorb)
- p<sub>4</sub> = 3V x 5A = 15W (absorb)
- p<sub>1</sub> + p<sub>2</sub> + V<sub>3</sub> + p<sub>4</sub> = 0 (conservation of power)