# Class 13: I/O 3 - UART and ADC-DAC
## Programmable Communications Interface: 16550
- Two separate sections are responsible for data communications: reciever and transmitter
- Can function in:
	- Simplex; transmit only
	- half-duplex: transmit and receive but not simultaneously
	- full-duplex: transmit and recieve simultaneously
### Pinout
A<sub>0</sub>, A<sub>1</sub> and A<sub>2</sub>: Select an internal register for programming and data transfer