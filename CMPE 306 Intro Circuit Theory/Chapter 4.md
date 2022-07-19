# Chapter 4 Circuit Theorems
## Linear Systems (Circuits)
- System's physical laws are linear
- System response is linearly proportional to the source magnitude.
- KVL, KCL, Ohm's law are all linear physical laws.
## Superposition Principle
- In a linear system, the total response due to multiple independent sources equals the algebraic sum of the responses due to each individual independent source
-  Example:
	- ![[Pasted image 20220222101341.png]]
	- If you deactivate I<sub>s</sub>, meaing i<sub>s</sub> = 0, then the circuit response due to V<sub>s</sub> is an open circuit 
	- ![[Pasted image 20220222102059.png]]
	- If you deactivate V<sub>s</sub>, meaning V<sub>s</sub> = 0, then the circuit response due to I<sub>s</sub> is a short circuit.
	- ![[Pasted image 20220222102117.png]]
## Source Transformation
- Generally, a voltage source is in series with a resistor R<sub>s</sub> and a current source is in parallel with a resistor R<sub>p</sub>. 
- They can be equivalent by source transformation
## Transformation of Dependent Sources
- (Provide that the original v<sub>s</sub> or i<sub>s</sub> dependence on v<sub>x</sub> or i<sub>x</sub> is not lost.)
- ### Deriviation
	- Consider a load Resistor R<sub>L</sub> is connected between terminals a-b.
	- If load is open circuit (R<sub>L</sub> = $\infty$): v<sub>ab,open</sub> = v<sub>s</sub> = R<sub>p</sub>i<sub>s</sub>
	- If load is short circuit (R<sub>L</sub> = 0): i<sub>ab,short</sub> = $\frac{v_s}{R_s}$ = i<sub>s</sub>
- Note that the transformation is valid for "generic" source configurations, while they do not necessarily represent good real sources
- Good real voltage sources have very small internal serial resistance R<sub>s</sub>
- R<sub>s</sub> = 0 for ideal voltage sources.
- Good real current sources have very large internal parallel resistance R<sub>p</sub>
- R<sub>p</sub> = $\infty$ for ideal current sources.
- ==Source transformation is useful for simplification of circuit analysis, not necessarily realistic implementation.==
	- For example, a very good voltage source with very small R<sub>s</sub> would be transformed to a current source with huge current in parallel with very small resistance.
	- It is mathematically equivalent, but not realistic.
## Thevenin Theorem
- ![[Pasted image 20220222111106.png]]
- Thevenin equivalent (modeled with respect to terminal a-b)
- ![[Pasted image 20220222111154.png]]
- ### Finding Thevenin Voltage V<sub>TH</sub>
- ![[Pasted image 20220222111246.png]]
### Finding Thevenin Resistance R<sub>TH</sub>
1. Deactivate all independent sources (rule number one)
2. Calculate R<sub>TH</sub> = R<sub>eq</sub> seen into the network at the designated terminals
- ![[Pasted image 20220222111453.png]]
- Without dependent source:
	- R<sub>eq</sub> = combination of passive resistances
- When there is a dependent source in the network, use the test-source method, and
	- R<sub>TH</sub> = R<sub>eq</sub> = $\frac{v_{test}}{i_{test}}$
	- ![[Pasted image 20220224100839.png]]
## Norton Equivalent
- ![[Pasted image 20220224102037.png]]
- I<sub>N</sub> = i<sub>ab,SC</sub>
- R<sub>N</sub> = R<sub>TH</sub>
- V<sub>TH</sub> = v<sub>ab,OC</sub>
- V<sub>TH</sub> = R<sub>TH</sub>I<sub>N</sub> -> by source transformation
- R<sub>TH</sub> = $\frac{v_{ab,OC}}{i_{ab,SC}}$
- Thevenin and Norton equivalents can be converted from each other by source transformation
## Maximum Power Transfer
- ![[Pasted image 20220224110343.png]]
- Simplify the driver circuit to its Thevenin equivalent
- ![[Pasted image 20220224110417.png]]
- i<sub>L</sub> = $\frac{V_{TH}}{R_{TH} + R_{L}}$
- P<sub>L</sub> = R<sub>L</sub>i<sub>L</sub><sup>2</sup> = R<sub>L</sub>$(\frac{V_{TH}}{R_{TH} + R_{L}})$<sup>2</sup>
- 