# FPGA vs. ASIC Design
## ASIC - Application Specific ICs
- An implementation in hardware of a specific function using digital and analog functions
- Gate cells are predesigned
	- Provided as library
		- Liberty file
		- LEF and DEF
- Can only be implemented once
## FPGA - Field Programmable Gate Array
- Reprogrammable, in-system programmable (ISP)
- Can be used the same as ASICs are
- Are restricted to whats given 
- Diverges from ASIC by where the route is done
- Could limit the amount of ICs that you need on your board
- Could be cheaper to manufacture FPGAs
- Wastes power to allow for all wiring configs
- Adds leakage current and power
## COTS - Commerical Off the Shelf
# HDL Code Styles
## Structural
## Behavioral
- Implicitly defines existence of registers (sequential) and the combinatiorial