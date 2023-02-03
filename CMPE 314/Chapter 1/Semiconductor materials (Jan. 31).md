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
# Semiconductor Energy Bands
- ![[Pasted image 20230202144900.png]]
- Due to atom interactions in a crystal, discrete atomic energy levels change to separate energy bands
- Inner shell electrons fill lower-energy bands
- Valance electrons fill the valance band.
- **Generation of free electrons and mobile holes**:
	- A valance electron gaining sufficient energy ($>E_g$) is lifted into the conduction band to become free electron
	- a positively charged empty state is lefted in the valance band, which is a mobile hole
## Energy Band Diagrams of Semiconductors
- Seen in 02/02 notes
- Bandgap energy $E_g$: 
	- Very large 3~6 eV -> insulator
	- small ~ 1eV -> semiconductor
	- conduction band is half-filled -> conductor
# Generation of Mobile Electrons and Holes
## Intrinsic Semiconductors:
- Covalent bonds are broken (quantum nature) (difficult but not possible)
- Electrons are lifted from valance band to conduction band, left with holes in valence band.
- Mobile electrons and holes are generated in equal amount
- Electrons and holes are generated in equal amount (remember this)
- ![[Pasted image 20230202145833.png]]
## Extrinsic Semiconductors
- ![[Pasted image 20230202150342.png]]
### n-type Semiconductors:
- Covalent bonds are not broken. 
- Extra valance electrons are lifted from the donor atom level (slightly below) to the conduction band. 
- Mobile electrons are generated in the conduction band (in this process no generation of holes in valence band)
- ![[Pasted image 20230202150902.png]]
- ![[Pasted image 20230202150407.png]]
### p-type Semiconductors:
- Covalent bonds are not broken.
- Electrons are lifted from valence band to the acceptor atom level (slightly above). 
- Mobile holes are generated in the valence band (in this process no generation of electrons in conduction band)
- ![[Pasted image 20230202150911.png]]
- ![[Pasted image 20230202150416.png]]
# Excess Carriers
- Carriers generated by mechanisms other than thermal excitation
- ![[Pasted image 20230202152302.png]]
- For example, when high energy photons are incident on a semiconductor, electrons can be lifted from the valence band to the conduction band, producing electron-hole pairs.
- ![[Pasted image 20230202152329.png]]
## Electron-hole recombination
- A free electron may recombine with a hole -> reducing the excess electrons and holes
- The mean time over which an excess electron and hole pair exist before recombination is called the excess carrier lifetime. In the steady state, electron-hole generation is balanced by the electronhole recombination.
# Currents in Semiconductor
## Drift Current 
- Movement of charges caused by an applied electric field
- ![[Pasted image 20230202153320.png]]
- ![[Pasted image 20230202153334.png]]
- ![[Pasted image 20230202153340.png]]
- ![[Pasted image 20230202153349.png]]
  ## Diffusion Current
  - With diffusion, particles flow from region of higher concentration to region of lower concentration
  - ![[Pasted image 20230202153427.png]]
  - Statistically, electrons (holes) move at an average speed determined by the temperature, in random directions and with equal probability in any direction. There are more particles in higher concentration region than in lower concentration region.
	  - Net flow of particles moving from the high concentration region toward the low concentration region
- ![[Pasted image 20230202153520.png]]