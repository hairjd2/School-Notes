# Definition of the DTFT
- ![[Pasted image 20240929231412.png]]
- Also use integration for DTFT like we do in CTFT
- The second implementation is not the best for computer calculation since its an infinite sum
- Gonna look at trying to make that second expression implementable on a computer
- ![[Pasted image 20240929232023.png]]
## DTFT of One-Sided Exponential Signal
- ![[Pasted image 20240929232424.png]]
- ![[Pasted image 20240929232510.png]]
- ![[Pasted image 20240929232845.png]]
## Inverse DTFT Example
- Euler's inverse identity: ![[Pasted image 20240929233237.png]]
- ![[Pasted image 20240929233304.png]]
- sinc function like seen in CTFT
- ![[Pasted image 20240929233524.png]]
- ![[Pasted image 20240929233536.png]]
- Problem at n=0 bc sin(0)=0 and 0/0 is not doable
- ![[Pasted image 20240929233753.png]]
## Finding the DTFT of Finite Length Signals
- ![[Pasted image 20240929234156.png]]
- Factor out the half angle
- ![[Pasted image 20240929234344.png]]
- Bc you have a e^j and e^-j gives you a ratio of sin's
- ![[Pasted image 20240929234359.png]]
### "Computing" the DTFT for Finite Length Sequences
- Relationship with finding DTFS
- ![[Pasted image 20240929234614.png]]
# Properties of the DTFT
- ![[Pasted image 20241001220342.png]]
- Periodicity: DTFT is equal at every frequency + 2xpi
- If the time domain signal is real-valued, then the DTFT has Hermitian Symmetry
	- If you look at the positive and negative frequency, they are complex conjugates of each other
- Time Shift: should get a linear phase factor multiplied by the original DTFT
	- Has no effect on the magnitude, which makes sense
	- You then see that the DTFT is completely real-valued (in the example)
- Frequency Shift: If you multiply signal by a complex sinusoid, the frequency content is shifted in the frequency domain
- ![[Pasted image 20241001221624.png]]
- Convolution works the same as in a CTFT
- Multiplication also leads to convolution of the fourier transforms, but only for a 2pi interval
- Can find the energy of the signal by integrating from -pi to pi of the magnitude of the fourier transform squared bc of Parseval
# Relating the Fourier-Domain Representations
- ![[Pasted image 20241001223300.png]]
## Periodic in Time
- Review: periodic in time is for Fourier Series
- For continuous time, the summation is infinite
- For DT, the summation is finite
- No need to look past the number of samples in the period for a DT signal since you would just be adding the same values again
## Aperiodic in Time
- No notes
## Characteristics of Fourier-Domain Representations
- If time-domain signal is CT, then the frequency domain is aperiodic
- If time-domain signal is DT, then the frequency domain is periodic with period 2pi
	- Shown by periodicity principle
- If td signal is periodic, then the fd signal must be discrete
- If td signal is aperiodic, then the fd signal must be continuous
- ![[Pasted image 20241001224615.png]]
# LTI Systems Analysis using the DTFT
- ![[Pasted image 20241001230507.png]]
-  ![[Pasted image 20241001230732.png]]
- ![[Pasted image 20241001231141.png]]
# Frequency Domain Analysis of Difference Equations
## IIR Systems and Difference Equations
- Consider a LTI system with the following impulse response $h[n]=a^nu[n],|a|<1$
- ![[Pasted image 20241001231857.png]]
- For IIR systems, not focused on convolution but difference equations
- ![[Pasted image 20241001231954.png]]
- Have a bunch of feedback terms for the first equation