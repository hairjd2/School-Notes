# Class 1
- [[#Syllabus|Syllabus]]
- [[#What is a computer|What is a computer]]
	- [[#CPU|CPU]]
- [[#Design Metrics|Design Metrics]]
- [[#Microprocessor:|Microprocessor:]]
- [[#Microcontroller|Microcontroller]]
- [[#Other Processing Chip Types|Other Processing Chip Types]]
	- [[#Single-Purpose Processor|Single-Purpose Processor]]
	- [[#Digital Signal Processor (DSP)|Digital Signal Processor (DSP)]]
	- [[#Application Specific Instruction-Set Processors (ASIPs or ASSPs)|Application Specific Instruction-Set Processors (ASIPs or ASSPs)]]
	- [[#Programmable Logic Devices (PLD)/Field Programmable Gate Arrays (FPGA)|Programmable Logic Devices (PLD)/Field Programmable Gate Arrays (FPGA)]]
	- [[#Application Specific Integrated Circuits (ASICs)/System-on-a-chip (SOCs)|Application Specific Integrated Circuits (ASICs)/System-on-a-chip (SOCs)]]
- [[#Evolution of computers|Evolution of computers]]
- [[#Levels of Programs:|Levels of Programs:]]

## Syllabus
- Tells joke in beginning of class
- Don't plagarize code
- Summary of class
	- Assembly language programming (Intel x86)
	- General system design concepts, devices and support chips
	- Specifically covers architecture of intel microprocessors
	- Hardware configuration and control of:
		- common microprocessor support chips like Interrupt controller, DMA controller
	- Popular I/O devices, e.g. UART, parallel IO, timers
- Expected to know
	- Experience with the C programming language
	- Some familiarity with OSs, like Windows
	- Experience with Linux
- Best to reach him by text #number: 484-554-3661
- #Textbook: Barry B. Brey, 'The Intel Microprocessors' Eighth Edition, Pearson/Prentice Hall (2009).
- Projects and labs: 
	- Assembly programming
	- Hardware project (board design and programming)
- Why did Mr. Ohm marry Mrs. Ohm, because he couldn't resist her; their love was current; 
- Final
	- Will be comprehensive
	- Can take it early

## What is a computer
- ![[Pasted image 20220131180639.png]]
### CPU
- Composes of the Arithmetic logic unit (ALU) which performs arithmetic and logic operations
- Also composes of the control unit (CU) which:
	- Fetches instructions from memory
	- decodes them
	- executes then
	- Calls upon ALU when needed

## Design Metrics
- NRE cost (nonrecurring engineering cost): one-time monetary cost of designing the system
- Unit cost: The monetary cost of manufacturing each copy of the system
- Size: The physics space required by the system
- Performance: The execution time of the system
- Power: The amount of power consumed by the system, which may determine the lifetime of the battery or the cooling requirements
- Flexibility: Ability to change the function of the system and software
- Time-to-prototype: Time to design, verify, and refine
- Time-to-market
- Maintainability: the ability to modify it after release
- Correctness: Confidence that we have implemented the system's functionality correctly
- Safety

## Microprocessor:
- Single VLSI chip that has a CPU and may also have other units that are additionally present and result in faster processing of instructions
- Examples:
	- Intel 8085
	- x86 processors
	- Intel Core i3, i5, i7, i9
	- Motorola 68hCxxx
	- AMD Athalon, Duron, Ryzon
	- IBM Espresso
	- Q
	- ARM Cortex-A9

## Microcontroller
- A single chip unit which, though having limited computational capabilities, possesses enhanced input-output capabilities and a number of on-chip functional units
	- particularly suited for use in embedded systems for real-time control applications with on-chip program memory and devices

## Other Processing Chip Types
### Single-Purpose Processor
- A digital circuit designed to execute exactly one program
- Commonly referred to as coprocessor, accelerator or peripheral
- Examples: JPEG codec, serial-to-ethernet convertor
### Digital Signal Processor (DSP)
- Essential for systems that require large number of operations on digital signals which are the digital encoding of analog signals
- Carries out common signal processing tasks like signal filtering, transformations or combinations
- Used widely in image processing applications, multimedia, audio, video, HDTV, DSP modem and telecommunication processing systems
- They perform math-intensive operations, including operations like multiply and add or shift and add etc.
- Examples:
	- TI TMS320Cxx 
	- Analog Devices SHARC
	- Motorola 5600xx
### Application Specific Instruction-Set Processors (ASIPs or ASSPs)
- Programmable processor optimized for a particular class of applications having common characteristics. Microcontrollers and DSPs can be considered as ASSPs
- ASIPS are available for broad application classes (e.g. graphics processor) as well as very small application classes, some as small as a handful of programs
- Example: ASSP chip with TCP, UDP, IP, ARP, and Ethernet 10/100 MAC logic
### Programmable Logic Devices (PLD)/Field Programmable Gate Arrays (FPGA)
- Contains general purpose logic elements that can be programmed to implement desired functionality, very flexible for implementing custom logic circuits
- PLD usually are smaller and contain programmable gates like AND/OR arrays
- FPGAs provide lot more functionality and can be used to implement complex designs
- FPGAs can have on-chip microprocessors, memory, DSP, communication devices
- Examples:
	- Xilinx Virtex
	- Spartan series FPGAs
	- Actel
	- Altera
	- Lattice
	- QuickLogic
### Application Specific Integrated Circuits (ASICs)/System-on-a-chip (SOCs)
- Custom designed VLSI chips that perform the required function
- Functionality can be integrated using IP (Intellectual property) cores
- General purpose processors are also available as IP cores and can be integrated on the chip
- Embedded processors are available from ARM, Intel, TI and various other vendors
- Only feasible for high volume, relatively high cost systems as NRE costs and time-to-market can be significant
## Evolution of computers
- ==Moore's Law==: Transistor density on integrated circuits doubles about every two years
1. 'x86 Evolution
2. i3, i5, i7 (i9)
3. Intel launches Tiger Lake: Up to 4.8 GHz, LPDDR4 Memory, Iris Xe Graphics up to 1.35 GHz
4. Intel launches 11th Gen Core mobile processors with Iris Xe
## Levels of Programs:
1. Hardware-Registers (programmed by rewiring)
2. 1st GL - Machine Language (Opcode)
3. 2nd GL - Assembler (Unique to the machine)
4. 3rd GL - High-Level Language (C or Pascal)
5. 4th GL - Higher level language (Advanced programming concepts)
6. 5th GL - Computer aided software engineering (CASE)
7. Application Programs
- Opcode is in binary, with a MNEMONIC keyword
- ![[Pasted image 20220131184515.png]]