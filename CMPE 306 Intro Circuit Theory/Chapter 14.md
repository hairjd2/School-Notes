# Chapter 14 Circuit Frequency Response
- ![[Pasted image 20220414100531.png]]
- $\bar{V_o}(\omega)=\bar{V_s}(\omega)\frac{1/j\omega C}{R+1/j\omega C}=\bar{V_s}(\omega)\frac{1}{1+j\omega RC}$
- $H(\omega)=\frac{Y(\omega)}{X(\omega)}$
- Where $X(\omega)$ is the input or source
- and $Y(\omega)$ is the output or response
- $H(\omega)=$ Voltage Gain $=\frac{V_o(\omega)}{V_i(\omega)}$
- $H(\omega)=$ Current Gain $=\frac{I_o(\omega)}{I_i(\omega)}$
- $H(\omega)=$ Transfer Impedance $=\frac{V_o(\omega)}{I_i(\omega)}$
- $H(\omega)=$ Transfer Admittance $=\frac{I_o(\omega)}{V_i(\omega)}$
- $s \equiv j\omega$ --- ==complex frequency==
## Low-pass Filter Circuits
### RC Circuit
- ![[Pasted image 20220421101734.png]]
- ![[Pasted image 20220421103921.png]]
- $|\bar{H}(\omega=\omega _c)|\equiv\frac{H_{max}}{\sqrt{2}}$
- RC filter: $\omega _c = \frac{1}{RC}$
### RL Circuit
- ![[Pasted image 20220421103454.png]]
- RL Filter: $\omega _c = \frac{R}{L}$
- ==Standard first-order low-pass filter transfer function==
	- $\bar{H}(s)=H_{max}[\frac{\omega _c}{s+\omega _c}]$
	- $\omega _c = \frac{1}{\tau}$
## High-pass Filter Circuits
### RC Circuits
- ![[Pasted image 20220421103736.png]]
- ![[Pasted image 20220421104021.png]]
- RC filter: $\omega _c = \frac{1}{RC}$
### RL Circuit
- ![[Pasted image 20220421104056.png]]
- RL Filter: $\omega _c={R}{L}$
- ==Standard first-order high-pass filter transfer function==
	- $\bar{H}(s)=H_{max}[\frac{s}{s+\omega _c}]$
	- $\omega _c = \frac{1}{\tau}$
## Bandpass Filter Circuits
### Serial RLC Circuit
- ![[Pasted image 20220421105803.png]]
- $Q \equiv \frac{\omega _0}{B}$ --- quality factor
- Serial RLC Filter: $Q=\sqrt{\frac{L}{R^2C}}$
- For standard second-order bandpass filter transfer function
- $\bar{H}(s) = H_{max}[\frac{Bs}{s^2+Bs+\omega _0^2}]$       $(B=2\alpha)$
## Band-stop Filter Circuits
### Serial RLC Circuit
- Standard second-order band-stop filter transfer function:
	- $\bar{H}(s) = H_{max}[\frac{s^2+\omega_0^2}{s^2+Bs+\omega_0^2}]$   
	- $(B=2\alpha)$
## Resonance
- At the resonance frequency the circuit behaves as a resistor (real) circuit, namely, the transfer function is purely real.
- 