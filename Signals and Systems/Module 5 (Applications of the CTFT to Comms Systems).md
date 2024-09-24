# Intro to Comms and and Carrier Modulation
- ![[Pasted image 20240923210258.png]]
## Communication System
- Purpose is to Tx a message signal m(t) over a channel to the end user
- ![[Pasted image 20240923212835.png]]
## Carrier Modulation
- Refers to the process by which some characteristic of a high frequency carrier signal is varied in accordance with the message signal
	- Sinusoidal carriers are most commonly used in analog modulation systems, $A(t)cos[\theta(t)]$
	- **Amplitude modulation**: the amplitude A(t) of the carrier is varied with the message signal m(t)
	- **Angle modulation**: the angle theta(t) of the carrier is varied with the message signal m(t). The most common example for analog communications is **Frequency Modulation (FM)**
- ![[Pasted image 20240923213403.png]]
- Just doing AM analysis in this course
### Reasons for Carrier Modulation
- Shift the spectral content of the message signal into the operating frequency band of the communication channel
	- Antenna size is proportional to some fraction of the wavelength of the electromagnetic signal
	- Impractical to do: ![[Pasted image 20240923213751.png]]
	- So need to maybe transmit in higher frequencies
	- Propagation effects
- Permits the simultaneous sharing of he same communication channel by many users
	- Frequency Division Multiplexing (FDM)
	- By shifting frequencies you can share one channel among many frequencies
# Double Sideband Suppressed Carrier (DSB-SC)
## Time Domain
- $m(t)cos(\Omega _ct)=m(t)cos(2\pi F_ct)$
- ![[Pasted image 20240923235307.png]]
- Typically highest frequency for audio is a couple kilohertz
- Highest FM is a few megahertz
- Remember when we did this with MLS and using an envelope to carry a message and change phase
## Frequency domain
- ![[Pasted image 20240923235602.png]]
- ![[Pasted image 20240923235612.png]]
- Common that Fourier transform will be symmetrical since its common for it to be real-valued
- When $F_c >> B$, then it gets shifted like the two signals on the right
- Upper sideband (USB) and Lower Sideband (LSB)
- No discrete frequency component at $F_c$ and $-F_c$
## Synchronous Demodulation of DSB-SC
- ![[Pasted image 20240924000040.png]]
- $p(t)=m(t)[cos(\Omega _ct)]^2-\frac{1}{2}m(t)[1+cos(2\Omega _ct)]$
- ![[Pasted image 20240924000307.png]]
- ![[Pasted image 20240924000315.png]]
- ![[Pasted image 20240924000320.png]]
- Out side signals rejected by low pass filter, giving the end result of the message, half of it
## Phase Mismatch in Synchronous Demodulation
- ![[Pasted image 20240924000803.png]]
- ![[Pasted image 20240924000821.png]]
- If the theta is close to 90 degrees, you could have an amplitude of 0
- DSB-TC alleviates need for phase and frequency match, simplifying perplexity of the rx, approach taken by broadcast AM
# Double-Sideband Transmitted Carrier (DSB-TC)
- Add a DC bias
- Consider adding a constant A to the message signal prior to amplitude modulation:
	- $[A+m(t)]cos(\Omega _ct)$ where A is chosen such that $A+m(t)\ge 0\forall t$
	- ![[Pasted image 20240924001424.png]]
- ![[Pasted image 20240924001718.png]]
- When you have it never go negative, everything that rides long the peak is just the message
- ![[Pasted image 20240924001748.png]]
- Can now just follow the envelope
- What happens when A isn't large enough: ![[Pasted image 20240924001821.png]]
- ![[Pasted image 20240924001928.png]]
## Asynchronous Demodulation of DSB-TC
- ![[Pasted image 20240924002055.png]]
- ![[Pasted image 20240924002245.png]]
- Part of transmit power is used for transmitting irrelevant signals for the power, leading to efficiency
- 