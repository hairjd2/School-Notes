- ![[Pasted image 20241002202004.png]]
- The process of taking a CT signal every certain amount of seconds
- Sampling induces an ambiguity in the absence of a priori info
- Uniform sampling in time
	- Samplign converts a ct signal into a dt signal
	- Uniform sampling with sampling interval $T_S$ and sampling rate or frequency $F_S=\frac{1}{T_S}$
	- Want to consider:
		- If the samples of x[n] accurately represent the ct signal $x_a(t)$
		- If possible, how to recover $x_a(t)$
		- How the sampling interval $T_S$ is selected
# Sampling Sinusoids
- ![[Pasted image 20241002202540.png]]
- $\Omega_0=2\pi F_0$
- $n=\frac{t}{T_S}$ <- normalized time
- Normalized frequency: $\omega_0=2\pi\frac{F_0}{F_S}$
- When there is a 1:1 relationship between CT and DT, that is the requirement for removing ambiguity
- Having frequencies be less than half the sampling rate forms the basis for the Ideal Sampling Theorem
- ![[Pasted image 20241002203432.png]]
	- Red dotted curve is the DT sampled signal
	- Can remove ambiguity by constraining the frequency of the CT signal
# Relationship Between CTFT and DTFT via Sampling
- ![[Pasted image 20241002203846.png]]
- ![[Pasted image 20241002204536.png]]
- ![[Pasted image 20241002204704.png]]
# Ideal Sampling Theorem
- When you sample in time, the CTFT is simply replicated
- ![[Pasted image 20241002205248.png]]
- Nyquist sampling rate, lowest rate possible at twice the highest frequency of the CT signal
- When a signal is bandlimited, it puts a constraint on how fast it changes in time
# Anti-Aliasing Filters
- ![[Pasted image 20241002205922.png]]
- If we aren't sure what the characteristics are of the signal we want to sample, a common technique is to pass it through a CT filter, usually low pass, to make sure that it is bandlimited
- ![[Pasted image 20241002210153.png]]
- ADC conversion
# Sample Reconstruction
- ![[Pasted image 20241002225515.png]]
- Bottom is often called sinc-interpolation
- ![[Pasted image 20241002230049.png]]
- ![[Pasted image 20241002230103.png]]
# Undersampling and Aliasing
- 