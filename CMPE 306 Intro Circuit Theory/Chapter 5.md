# Chapter 5 Operational Amplifiers
- Op-amps are ICs that contain advanced electronic parts like transistors.
- It is typically packaged as a multi-pin device
- The important pins are: 
	- two inputs (2,3)
	- One output (6)
	- and two power supply bias (4, 7)
## Non-ideal op-amp internal circuitry
- ![[Pasted image 20220301101853.png]]
- V<sub>n</sub>: input voltage at the inverting terminal (measured above ground)
- v<sub>p</sub>: input voltage at the non-inverting terminal (above ground)
- v<sub>o</sub>: output voltage (measured above ground)
- v<sub>d</sub> $\equiv$ v<sub>p</sub> - v<sub>n</sub>: difference between two input voltages
- v<sub>o,oc</sub> = Av<sub>d</sub>: open circuit output voltage
- R<sub>i</sub>: equivalent input resistance
- R<sub>o</sub>: equivalent output resitstance
- ![[Pasted image 20220301101927.png]]
## Inverting Amplifier with op-amp internal circuit
- ![[Pasted image 20220301103005.png]]
- ![[Pasted image 20220301103022.png]]
- In comparison to A, R<sub>i</sub>, R<sub>f</sub>, or R<sub>s</sub>, constants and R<sub>o</sub> can be neglected due to how much smaller they are
## Ideal op-amp device law: 
- A -> $\infty$, R<sub>i</sub> -> $\infty$, R<sub>o</sub> -> $\infty$ 
- v<sub>p</sub> = v<sub>n</sub>
- i<sub>p</sub> = 0, i<sub>n</sub> = 0
- For inverting amp, v<sub>p</sub> = 0
- ![[Pasted image 20220301104148.png]]
- For non-inverting amp, v<sub>p</sub>
- ![[Pasted image 20220301110915.png]]
## Ideal Op-amp Circuit
- Removes the need for the resistor in thevenin circuit
- For ideal op-amp circuits, R<sub>th</sub> =0, while v<sub>TH</sub> = v<sub>o,oc</sub>.
- So they act as ideal voltage sources 
- Output voltage v<sub>o</sub> maintains the same even when a load circuit is connected
- If a load resistor R<sub>L</sub> is connected the load current is:
	$i_{L} = \frac{v_{o}}{R_{L}}$
- 