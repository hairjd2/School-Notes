# ASIC
- Four main classes:
	  1. Gate Arrays
	  2. Structured ASICs
	  3. Standard cell devices
	  4. Full-custom chips
## Full-custom
	- Nothing is predefined, not even standard logic gates
## Gate Arrays
- Based on the idea of a basic cell consisting of a collection of unconnected transistors and resistors
- ASIC vendor "prefabs" silicon chips containing arrays of these basic cells
- Channels are typically provided between rows or columns of these arrays for routing
- Cell library also provided by vendor
- Used up to around the 2000's
## Standard Cell Devices
- Makes templating cells easy
- Similar to gate arrays, the ASIC vendor defines the cell library
## Structured ASICs
# FPGA
- Based on CMOS technologies
## Early chips
- Based on CMOS and and used SRAM cells for configuration
- used an array of programmable logic blocks (PLBs)
- PLB arrays comprised of 3-input (lookup table) LUT, a register and a mux
## Today's
- More complex
- An FPGA might also have a global (high-speed) interconnection network
- This allows signals to cross the chip without having to pass through local switching elements
## FPGA-ASIC Hybrids
- Although it doesn't make sense to embed an ASIC inside an FPGA, the other way around works well
- This is useful for **platform design**
- Hard to dedseign because the design tools are significantly different between FPGA and ASIC
- ASIC: fine-grained; FPGA: medium-grained or coarse-grained