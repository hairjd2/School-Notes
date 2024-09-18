# Definition of the CT Fourier Transform
- ![[Pasted image 20240914173425.png]]
- CT Fourier Transform (CTFT) decomposition for aperiodic signals x(t):
	- $x(t)=\frac{1}{2\pi}\int_{-\infty}^{\infty}X(\Omega)e^{j\Omega t}d\Omega$
- Where the CTFT function is found via:
	- $X(\Omega)=\int_{-\infty}^{\infty}x(t)e^{-j\Omega t}dt$
	- ![[Pasted image 20240914211558.png]]
	- ![[Pasted image 20240916202643.png]]
- ![[Pasted image 20240916203028.png]]
- Double arrows means that its a Fourier Transform pair
- Omega is the radian frequency
- ![[Pasted image 20240916203201.png]]
	1. Having a larger a value means it will converge much quicker
	2. Much more spread out
- When a time domain signal changes more quickly in time, you need high frequency content to support that.
## Examples of CTFT Pairs
- Example 1: Rectangular Pulse
	- ![[Pasted image 20240916211005.png]]
	- ![[Pasted image 20240916211010.png]]
	- Pretty simple, lets us put it into terms of a
	- ![[Pasted image 20240916211124.png]]
	- Use Euler's identity: ![[Pasted image 20240916211138.png]]
	- ![[Pasted image 20240916211315.png]]
	- Results in a sinc function: ![[Pasted image 20240916211403.png]]
	- Notice that the 0 crossings occur at pi/a
	- The signal is diminishing 1/freq
	- As a gets large, the curve will get narrower and higher
- Example 2: CTFT of Unit Impulse: ![[Pasted image 20240916211719.png]]
	- ![[Pasted image 20240916212204.png]]
	- ![[Pasted image 20240916212211.png]]
	- Need relatively high frequencies to support it
## Convergence of the CTFT
- Sufficient conditions for the existence of the CTFT of x(t) are given by:
	- x(t) is absolutely integrable:
		- ![[Pasted image 20240916212308.png]]
		- Similarity to stability of LTI
	- x(t) has a finite number of maxima and minima with any finite interval
	- x(t) has a finite number of discontinuities within any finite interval, and each of these discontinuities is finite
## Inverse CTFT Examples
- 