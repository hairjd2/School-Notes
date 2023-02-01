# Syllabus
## Labs
- Have groups of 2 for lab and project
- Students will submit separate lab report and pre-lab
## Grading 
Need a 65 to pass, will have a 5% wiggle room
# Review (CMPE 306)
- Have KCL and KVL, which apply for any circuits
- Superposition principle is very important (review how to do this)
- **Thevenin** (this mainly) and norton very important
## What's new
- Still have KCL and KVL
- We now have diodes and transistors
### Circuit Theorems and Methods (Same)
- Independent sources and dependent sources (behavior of a transistor)
- Superposition principle
- Thevenin and Norton
- Equivalent resistance (particularly with dependent source)
- Circuit frequency response analysis
# Semi conductor materials
- Look to 01/31 for drawings
- Silicon is the most basic semiconductor material
- Si atom has 14 protons and neutrons in the centers, 14 electrons that orbit
- 10 on the inside, 4 on the outer shell
- **Valence electrons --- electrons reside in the partially filled outer shell**
- ![[Pasted image 20230131201323.png]]
- The silicon atoms get packed together super close
## Intrisinc material
- ![[Pasted image 20230131201524.png]]
- At 0 degress kelvin, the semiconductor will act as an insulator, no electrons will move
## Intrinsic material (T > 0 K)
- When energy is injected, the thermal energy can cause valance electrons to gain enough thermal energy to break the covalent bond and move away
- becomes free electrons
- Then an empty state is created meaning the neighboring valence electron can hop in and filly it in
- A positively charged "particle" is moving: hole
- ![[Pasted image 20230131202544.png]]
- The amount of moving electrons and holes generated are equal, two types of charged particles contribute to current
## Extrisic Semiconductors (Doped semiconductors)
- Semiconductor materials containing impurity atoms.
### N-type
- Silicon doped with phosphorus atom (group V)
- ![[Pasted image 20230131203259.png]]
- The fifth valance electron is more loosely bound to the phosphorus atom (by the Coulomb force) and at room temperature gains sufficient thermal energy to very easily break the Coulomb bond.
- The phosphorus atom
	- A donor impurity (donates an electron that is free to move).
- Free electrons are created from donor atoms without generating holes (covalent bonds not broken in this process)
- "Positive" phosphorus atoms cannot move and do not contribute to current
### P-type
- Silicon doped with boron atom (group III)
- ![[Pasted image 20230131203847.png]]
- Since there is a missing covalent bond from boron (initial empty state), that means that there must be a valence electron that moves to fill in that initial hole
- Creates a mobile hole
- Three valance electrons of boron contribute to three covalent bonds; one covalent bond position is open. At room temperature adjacent silicon valance electron has sufficient thermal energy to move into this position (empty state from the acceptor atom).
- Creation of mobile holes from acceptor atoms without generating free electrons (covalent bonds not broken in this process)
- "negative" boron atoms cannot move and do not contribute to current