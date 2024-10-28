- "When a signal is discrete, it can be thought of as a list of numbers representing the sample values of an analog waveform."
- One pulse is placed at each sampling point
# Pulse Modulation
## PAM (Pulse Amplitude Modulation)
- Flat-top PAM (s(t) inputted into a gating circuit):![[Pasted image 20241022210617.png]]
- Natural PAM (simply a product of the pulse train and s(t)):![[Pasted image 20241022210640.png]]
- Time Division Multiplexing
	- Need a way to allow multiple channels talk over one single channel
	- Divide by time for each seperate source
	- Time required for switch to stop is the fraction of time required for each PAM signal
	- ![[Pasted image 20241022213955.png]]
	- Is a linear form of modulation
- Can be susceptible to crosstalk due to overlap of time slots
- 
## PWM (Pulse Width Modulation)
- Pulse width not constant, so power of waveform not constant
- As amplitude increases, power transmitted also increases
- Complex to find FT bc it is a nonlinear form of modulation
	- This is because the second modulated wave should be relative to the first wave
	- Linearity would dictate that the waveform really be the size of the dotted lines![[Pasted image 20241022215339.png]]
- Can use a sawtooth waveform to convert from PWM to PAM by converting from time to amplitude:![[Pasted image 20241022220225.png]]
- ![[Pasted image 20241022220315.png]]
- 
## PPM (Pulse Position Modulation)
- Has noise advantage like PWM but also no problem of a variable power that is a function of the amplitude of the signal
- Derived from PWM
	- For both, the position of the pulse varies
	- But for PWM, the location of the leading or trailing edge of the pulse varies
- 
# Binary Line Coding