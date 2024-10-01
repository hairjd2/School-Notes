# Summing Harmonically-Related CT Sinusoids
- ![[Pasted image 20240909153801.png]]
- MATLAB code to show it: ![[Pasted image 20240909153839.png]]
- ![[Pasted image 20240909210501.png]]
	- Has discontinuities, challenging to represent a discontinuity with a sinusoid
- ![[Pasted image 20240909210536.png]]
	- Lower bandwidth since something is happening quicker for the square wave
- Express in terms of Complex Exponentials
	- ![[Pasted image 20240909210743.png]]
	- ![[Pasted image 20240909210749.png]]
	- $sin(x)=\frac{1}{2j}(e^{jx}-e^{-jx})$
	- ![[Pasted image 20240909210919.png]]
	- ![[Pasted image 20240909211040.png]]
# Continuous Time Fourier Series
- The CT Fourier Series decomposition for periodic signals $x(t)=x(t+T_0)$
	- ![[Pasted image 20240909211229.png]]
- The complex numbers $X_k$ are called the ==Fourier Series Coefficients==
	- ![[Pasted image 20240909211348.png]]
- The Fourier series coefficients can be found by:
	- $X_k=\frac{1}{T_0}\int_{T_0}x(t)e^{-jk\Omega _0t}dt$
	- Use whatever period is most convenient
- k = 0 term:
	- ![[Pasted image 20240909211709.png]]
	- Average term or average x(t) over 1 period
- $k=\pm1$ terms are referred to as the fundamental or first harmonic
- $k=\pm2$ terms are referred to as the second harmonic
- Note that the Fourier series coefficients are associated with the "shape" of the periodic signal
- The period of the periodic signal is solely determined by the fundamental frequency $\Omega _0$
## Calculating the CTFS coefficients
- ![[Pasted image 20240909212453.png]]
- First find the k = 0 term
- Period to integrate over: ![[Pasted image 20240909212554.png]]
- ![[Pasted image 20240909212604.png]]
- ![[Pasted image 20240909212611.png]]
- So average value is $\frac{A}{2}$
- ![[Pasted image 20240909213355.png]]
- ![[Pasted image 20240909213402.png]]
- ![[Pasted image 20240909213446.png]]
## Amplitude and Phase Spectrum
- A plot of $|X_k|$ vs k (or freq) is called the amplitude spectrum
- A plot of the phase of $X_k$ vs k is called the phase spectrum
- Example
	- ![[Pasted image 20240909213710.png]]
	- k= -15 to 15![[Pasted image 20240909213842.png]]
## Alternative Forms of the CT Fourier Series
- Convert complex Fourier series to real Fourier series
- ![[Pasted image 20240909221504.png]]
- ![[Pasted image 20240909221602.png]]
- ![[Pasted image 20240909221632.png]]
- $X_k=X_{-k}$
- ![[Pasted image 20240909221715.png]]
- ![[Pasted image 20240909222151.png]]
- ![[Pasted image 20240909222211.png]]
- Trigonometric Fourier Series for a real-valued time signal:
	- ![[Pasted image 20240909222235.png]]
	- ![[Pasted image 20240909222244.png]]
	- Has sin and cos because a signal may not always be just even or odd
- Harmonic Fourier Series for a real-valued time signal:
	- Pointing to the phase angle ![[Pasted image 20240909222331.png]]
	- ![[Pasted image 20240909222349.png]]
## Properties of CT Fourier Series
- If x(t) is real-valued, then $X_k=X_k^*$, sometimes called Hermitian Symmetric
- ==Linearity==: If x(t) has CTFS coefficients $X_k$ and y(t) has CTFS coefficients $Y_k$, then x(t)+y(t) has CTFS coefficients $X_k+Y_k$
- ==Time Shift==: If x(t) has CTFS coefficient $X_k$, then x(t-t0) has CTFS coefficients $X_ke^{-j2\pi kt_0/T_0}$
	- If you find that magnitude, you would get a magnitude of the same $X_k$
- Parseval's Relationship:
	- ![[Pasted image 20240910215535.png]]
	- Find the power of the following real-valued sinusoidal signal: ![[Pasted image 20240910215554.png]]
	- ![[Pasted image 20240910215807.png]]
### Example: Shifted Periodic Square Wave:
- Odd: ![[Pasted image 20240910214848.png]]
- Even: ![[Pasted image 20240910214945.png]]
- $y(t)=2x(t-\frac{T_0}{4})-A$
	- ![[Pasted image 20240910215040.png]]
- $Y_0=2X_0-A=2(\frac{A}{2})-A=0$
- $Y_k=2X_ke^{-j2\pi k(\frac{T_0}{4})/4}=2X_ke^{-j\frac{\pi}{2}k}=2X_k(-j)^k$ (because $e^{-j\frac{\pi}{2}}=-j)$
- $X_k=\frac{sin(\frac{\pi}{2}k)}{\pi k}$
# Discrete-Time Fourier Series (DTFS)
- Discrete-time sinusoid:
	- $x[n]=A_0cos(\omega _0n+\theta)$
	- where A0 is amplitude, omega is angular frequency, and theta is phase
- Properties
	- x[n] is periodic if and only if omega0/2 is a rational number (a fraction)
		- If omega/2 = m/N is irreducible, then N is the fundamental period
	- DT sinusoids with radian frequencies omega separated by integer multiples of 2pi are identical
		- Increasing omega doesn't necessarily increase rate of oscillation
- k is harmonic index
- Form a lot of the techniques for DSP
- ![[Pasted image 20240910221120.png]]
- ![[Pasted image 20240910221135.png]]
## Properties
- ![[Pasted image 20240910222255.png]]
- The DTFS coefficients are also periodic => $c_k=c_{k+N_0}$
- If x[n] is real-valued, then $c_k=c_{N_0-k}=c_k^*$
- Parseval's Relation: $P=\frac{1}{N_0}\sum_{n=0}^{N_0-1}|x[n]|^2=\sum_{k=0}^{N_0-1}|c_k|^2$
- Time Shift: if x[n] <-> ck, then x[n-n0] <-> $e^{-j2\pi n_0k/N_0}$ck
# Frequency Response of CT LTI Systems
- Complex sinusoidal input to LTI Systems: ![[Pasted image 20240910223629.png]]
- ![[Pasted image 20240910223637.png]]
- When Omega naught is between negative Omega c and Omega c, y(t)=x(t)
- ![[Pasted image 20240910230508.png]]
- ![[Pasted image 20240910230528.png]]
- ![[Pasted image 20240910230710.png]]
## Periodic Inputs to CT LTI Systems
- ![[Pasted image 20240911195045.png]]
- ![[Pasted image 20240911195050.png]]
- Observations:
	- The output signal is periodic with the same period as the input signal
	- The Fourier series coefficients of the output signal are the coefficients of the input signal, modified by the system's frequency response at each constituent frequency:
	- ![[Pasted image 20240911195148.png]]
- ![[Pasted image 20240911195325.png]]
- ![[Pasted image 20240911200202.png]]
# Frequency Response of DT LTI Systems
- ![[Pasted image 20240910230909.png]]
- ![[Pasted image 20240910231028.png]]
- Non-ideal low pass filter: ![[Pasted image 20240910231055.png]]
- ![[Pasted image 20240910231118.png]]

## Periodic Inputs to DT LTI Systems
- ![[Pasted image 20240911201623.png]]
- 