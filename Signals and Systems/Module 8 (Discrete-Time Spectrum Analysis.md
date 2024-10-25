# Intro to Spectrum Analysis
- ![[Pasted image 20241009214815.png]]
- This will lead to DFT and even FFT
# Periodicity of Sunspots
## Computing the DTFT for Finite Length Sequences
- ![[Pasted image 20241014153145.png]]
- $2\pi<=>F_S$
## Application
- ![[Pasted image 20241014153302.png]]
- ![[Pasted image 20241014154031.png]]
- Keep idea in mind to increase density of samples to get more accurate results
# The Discrete Fourier Transform
- ![[Pasted image 20241014155534.png]]
- ![[Pasted image 20241014175120.png]]
- ![[Pasted image 20241014175135.png]]
## Properties of the DFT
- ![[Pasted image 20241014175621.png]]
- Denote that it is a DFT pair
- Seen before, when the DT signal is real-valued, then the FT representation has that conjugation equivalency
- Use FFT command in MATLAB to find DFT
- ![[Pasted image 20241014180242.png]]
	- ![[Pasted image 20241014180253.png]]
- The time shift occurs in a circular fashion
	- ![[Pasted image 20241014180608.png]]
	- In red x's ![[Pasted image 20241014180616.png]]
- Parseval's relationship as normal
# Computation and the FFT
- All are gonna be $e^{-j\frac{2\pi}{N}(integer)}$ and are gonna be precomputed
- N complex multiplies, N-1 complex additions
- ![[Pasted image 20241014184309.png]]
- ![[Pasted image 20241014184319.png]]
- Best when N is the some power of 2
- FFT Gain = N/log2N
- Can use the nextpow2 command
# Zero-padding and Dual-Tone Multi-Frequency Signaling (DTMF)
- ![[Pasted image 20241014185454.png]]
- ![[Pasted image 20241014191553.png]]
# Frequency Content of Musical Instruments
- ![[Pasted image 20241014195330.png]]
- $F_0$ represents the instrument's fundamental 'pitch'
# Frequency Leakage and Windowing
- ![[Pasted image 20241014211758.png]]
- Zero padding doesn't help in case 3
- ![[Pasted image 20241014214526.png]]
- The idea is to have a window that provides some sort of taper to improve our identification of the time domain signal
- ![[Pasted image 20241014214639.png]]
- Hamming window can help find weak sinusoidal signals with the presence of stronger ones