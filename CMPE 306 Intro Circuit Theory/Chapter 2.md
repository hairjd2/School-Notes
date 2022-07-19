# Chapter 2 Basic Laws
## Fundamental Laws
- Kirchhoff's current law
- Kirchhoff's voltage law
- KCL and KVL apply to any circuits containing any types of circuit elements
## Device Physical Laws
- I-V relationship (information) for individual elements
- Different types of circuit elements have different device laws
## Concepts of node, branch, loop, mesh
1. Node: a point at which two or more circuit elements join.
	- essential node: a point at which three or more circuit elements join
2. branch: a path that connects two nodes
	- essential branch: a path that connects two neighbor essential nodes.
3. loop: a closed path traversing through selected circuit elements and returning to the starting node
4. Mesh: a special loop that does not contain any loops within it
### Example
![[Pasted image 20220203105003.png]]
- Points a, b, c are nodes. Points b and c are essential nodes
- Paths between essential nodes b and ca re (4) essential branches
- Six loops can be formed
- There are three meshes
## KCL: At any instant of time, at any node:
- Write out equation later
- use + for i<sub>out</sub> and - for i<sub>in</sub>
- Applies to the conservation of charges
- Applies to a closed boundary (any electric circuit "box")
## KVL: At any instant of time, in traversing around a loop:
- Write out equation later
- use + for v<sub>drop</sub> and - for v<sub>rise</sub>
- KVL applies to the law of conservation of energy
## Ohm's Law
- Write out equation later
- $R = v/i$ 
## Series Resistors and Voltage Division
- Serial components share the same current
- Device law (Ohm's law): v<sub>1</sub> = R<sub>1</sub>i
- Combined with KVL: v = (R<sub>1</sub> + R<sub>2</sub> + ...)i
### Voltage Division (for strictly series resistors)
- The voltage drop at resistor R<sub>k</sub>
- v<sub>k</sub> = R<sub>k</sub>i = vR<sub>k</sub>/R<sub>eq</sub>
## Parallel Resistors and Current Division
- Device law (Ohm's law)
	- i<sub>1</sub> = v/R<sub>1</sub>
	- i = v/R<sub>eq</sub>
### Current Division (for strictly parallel resistors)
- i<sub>k</sub> = v/R<sub>k</sub> = iR<sub>eq</sub>/R<sub>k</sub>
### #ProvideTheSign
## Ammeter and Voltmeter
- ![[Pasted image 20220208104414.png]]
- ![[Pasted image 20220208104428.png]]
### Ammeter
- Basic meter unit (I<sub>m</sub> <= i<sub>m,max</sub>) in series with the circuit element
- If I > I<sub>m,max</sub>:
	- Modify with a parallel resistance R<sub>A</sub> for current division
- The V<sub>o</sub> in parallel is designated by the first one in example problem 2.7
## Key Points in Applying KCL/KVL and Device Laws
### KVL
- Trace a complete loop and identify all elements along the loop.
- Designate voltage polarity (can have options) for each element.
- "Sum" voltages for each element to zero.
- Distinguish signs for voltage rise and voltage drop (option: "+" for v<sub>drop</sub>, "-" for v<sub>rise</sub>)
### KCL
- Identify all branches at a node
- Designate current direction (can have options) in each branch.
- "Sum" currents to zero.
- Distinguish signs for current-in and current out (option: "+" for i<sub>out</sub>, "-" for i<sub>in</sub>)
### Laws for individual elements
- v = (+-)Ri
- p = (+-)vi
- ==Must== follow the passive sign convention for ==designated== voltage polarity and current direction (can have options for designation)
### Note:
Passive Sign Convention is not used "directly" in KVL/KCL. It is involved when express the voltage (or current) at a resistor by its current (or voltage) using Ohm's law, which takes default positive sign only when the current direction sees a voltage drop.
## Delta to Wye Conversion
- Delta<sub>block</sub> (R<sub>a</sub>, R<sub>b</sub>, R<sub>c</sub>)
- Wye<sub>block</sub> (R<sub>1</sub>,R<sub>2</sub>,R<sub>3</sub>)