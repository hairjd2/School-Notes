# Class 7: Memory
## Types
- Two basic types:
	- ROM: Read-Only Memory
	- RAM: Read-Write Memory
- Four commonly used memories:
	- ROM
	- Flash, EEPROM
	- Static RAM (SRAM)
	- Dynamic RAM (DRAM), SDRAM, RAMBUS, DDR RAM
## Memory Chips
- The number of address pins is related to the number of memory locations.
	- Common sizes today are 1k to 256M locations
	- Therefor between 10 and 28 address pins
- The data pins are typically bi-directional in read-write memories
	- The number of data pins is related to the size of the memory location
- Each memory device has at least one chip select or chip enable or select pin that enables the memory device
	- This enables read and/or write operations
	- If more than one are present, then all must be 0 in order to perform a read or write
- Each memory device has at least one control pin
	- For ROMs, an output enable or gate is present
	- For RAMs, a read-write or write enable and read enable are present
- ### ROM:
	- Non-volatile memory: maintains its state when powered down. There are several forms:
		- ROM: Factory programmed, cannot be changed, older style
		- PROM: Programmable Read-Only Memory. - Older style
			- Field programmable but:
				- May need a special programmer machine
				- May need to be removed from the system to do so
		- EPROM: Erasable Programmable Read-Only Memory
			- Reprogramming requires up to 20 minutes of high-intensivity UV light exposure.
		- Flash, EEPROM: Electrically Erasable Programmable ROM.
			- Also called EAROM (Electrically Alterable ROM) and NOVRAM (NOn_Volatile RAM)
			- Writing is much slower than a normal RAM
			- Used to store setup information, e.g. video card, on computer systems.
			- Can be used to replace EPROM for BIOS memory.
## SRAMs
- Virtual identical to the EPROM with respect to the pinout
- However acces time is faster (250ns)
	- See the timing diagrams and data sheets in text.
- SRAMS used for caches have access times as low as 10ns.
- SRAMS are limited in size 128k x 8
- DRAMS are available at 64Mx1
- DRAMs MUST be refereshed every 2 to 4 ms.
- The large storage capacity of DRAMs makes it impractical to add the required number of address pins.
	- Instead, the address pins are multiplexed RAS / CASD RAMs
## DRAMs
- The TMS4464 can store a total of 256K bits of data
- It has 64k addressable locations which means it needs 16 address inputs, but it has only 8.
	- The row address (A<sub>0</sub> through A<sub>7</sub>)are placed on the address pins and strobed into a set of internal latches
	- Column address (A<sub>8</sub> through A<sub>15</sub>) is then strobed in using CAS
- Larger DRAMs are available which are organized as 1M x 1, 4M x 1, 16M x 1, 64M x 1, 256M x 1
- DRAMs are typically placed on SIMM (Single In-line Memory Modules) boards
- Pentiums have a 64-bit wide data bus
- The DIMM module is available in DRAM, EDO and SDRAM (and NVRAM) with an without an EPROM
	- The EPROM provides information about the size and speed of the memory device for PNP applications
## DDR (s)
- Double Data Rate RAMs come in several different rates.
- DDR2 to DDR6
## Memory Address Decoding
- Each of the two RAMs shown has 8 data bits (1 byte) in each address
- The 4 address bits for each RAM (A<sub>3</sub> down to A<sub>0</sub>) then tells us that each RAM has 16 address locations each
- A<sub>4</sub> (The fifth bit) is used to tell which RAM chip to look at