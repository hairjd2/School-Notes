## Continuous Time Signal
- x(t)
- function of a continuous independent variable t (typically time)
- Represents some physical quantity
## Discrete-Time Signal
- x[n],n=...,-2,-1,0,1,2
- Function of a discrete independent variable n (typically time index) representing some physical quantity
- DT signals may occur naturally
- DT siognals may arise from sampling a CTS (digital audio)
## Finite vs Infinite Signals
- Finite length: 
	- $x(t) = 0, t<t_1\ and\ t>t_2$
	- $x[t] = 0,n<N_1\ and\ n>N_2$
- Infinite length two-sided, right-sided, or left sided:
	- ![[Pasted image 20240828233414.png]]
## Even vs Odd
- Even:
	- x(t) = x(-t)
	- ![[Pasted image 20240828233534.png]]
	- x[n] = x[-n]
	- ![[Pasted image 20240828233552.png]]
- Odd:
	- x(t) = x(-t)
	- ![[Pasted image 20240828233615.png]]
	- x[n] = x[-n]
	- ![[Pasted image 20240828233620.png]]
![[Pasted image 20240828233919.png]]
- E = P * T
# Signal Energy
## Example 1
- ![[Pasted image 20240829192241.png]]
- ![[Pasted image 20240829192358.png]]
- ![[Pasted image 20240829192405.png]]
- ![[Pasted image 20240829192626.png]]
## Example 2
- ![[Pasted image 20240829192647.png]]
- ![[Pasted image 20240829192653.png]]
- ![[Pasted image 20240829192849.png]]
- ![[Pasted image 20240829193324.png]]
# Time Transformation
- Works the same as in functions
- Time shift x(t-t0)
- Time Reversal x(-t)
- Compression x(t) -> x(2t)
- Expansion x(t) -> x(t/2)
# Real Exponentials
- CT exponentials:
	- ![[Pasted image 20240829200147.png]]
- DT exponentials:
	- ![[Pasted image 20240829200240.png]]
# Sinusoids
- CT sinusoid
	- $x(t) = Acos(2\pi Ft+\theta)$
	- $x(t) = Acos(\Omega t+\theta)$
	- Where A = amplitude, F = frequency, Omega = frequency, and theta = phase
	- x(t) period $T_p=\frac{1}{F}$
	- CT sinusoids with distinct features are distinct
	- Increasing F increases rate of oscillation
- DT Sinusoid:
	- $x[n]=A_0cos(\omega_0n+\theta)$
	- Where: A = amplitude, omega = normalized frequency, theta = phase
	- x[n] is periodic if and only if omega /2pi is a rational number
		- If omega/2pi = m/N is irreducible, then N is the fundamental period
	- DT sinusoids with radian frequencies omega separated by integer multiples of 2pi are identical
		- Increasing omega doesn't necessarily increase rate of oscillation
	- 
# Complex Exponentials
- $x(t)=Ae^{j(\Omega_0 t+\theta)}=Acos(\Omega_0 t+\theta)+jAsin(\Omega_0 t+\theta)$
- ![[Pasted image 20240829195508.png]]
- ![[Pasted image 20240829195514.png]]
- Can combine two complex sinusoid conjugates to just get the real sinusoid
- $x(t) = Acos(\Omega_t+\theta)=\frac{A}{2}e^{j(\Omega_0t+\theta)}+\frac{A}{2}e^{-j(\Omega_0t+\theta)}$
- ![[Pasted image 20240829195853.png]]
# Unit Impulse and Unit Step
## Basic DT Signals
- Unit impulse: ![[Pasted image 20240830183630.png]]
	- ![[Pasted image 20240830183710.png]]
- Unit step: ![[Pasted image 20240830183644.png]]
	- ![[Pasted image 20240830183717.png]]
- Properties:
	- ![[Pasted image 20240830183730.png]]
	- ![[Pasted image 20240830184058.png]]
	- Can represent any arbitrary signal by superposition of scaled and time delayed impulses
	- Above used in Limited Time Invariant system
## Basic CT Signals
- Unit Step: 
	- ![[Pasted image 20240830195353.png]]
	- ![[Pasted image 20240830195403.png]]
- One-sided exponential:
	- $e^{-\alpha t}u(t),\alpha>0$
	- ![[Pasted image 20240830195530.png]]
- Unit Impulse
	- Unit impulse in ct is typically defined as the limit of a signal having a unit area over an infinitesimal time interval
	- ![[Pasted image 20240830195620.png]]
	- $\delta(t)=0,t\ne0$
	- $\int_{-\infty}^{\infty} \delta(t)dt=1$
	- ![[Pasted image 20240830195935.png]]
	- Sifting property
		- ![[Pasted image 20240830200026.png]]
		- ![[Pasted image 20240830200032.png]]
		- ![[Pasted image 20240830200159.png]]
	- Time scaling: ![[Pasted image 20240830200234.png]]
	- Express arbitrary signal in terms of the unit impulse: ![[Pasted image 20240830200258.png]]
# Operations on Signals
- Signal Splitting: ![[Pasted image 20240830200425.png]]
- Signal Addition: ![[Pasted image 20240830200436.png]]
	- ![[Pasted image 20240830200534.png]]
- Amplitude Scaling: ![[Pasted image 20240830200448.png]]
	- ![[Pasted image 20240830200732.png]]
- Signal Multiplication: ![[Pasted image 20240830200458.png]]
	- ![[Pasted image 20240830200751.png]]
# Systems
- A CT system H maps an input CT signal x(t) into an output CT signal y(t)
- CT system components are physical devices with IO characteristics determined by the underlying physics governing their operation
- Resistors, capacitors, inductors, etc.
- An example would be an RC circuit 
- A DT system maps input DT signal x[n] into output DT signal y[n]
- DT systems are comprised of basic digital computer components such as adders, multipliers, and storage elements
- Advantages over CT systems
	- Robustness of digital hardware
	- Increased flexibility
	- Increased efficiency
	- Increased performance
## Classification
- Memory and memoryless: A system is memoryless if the output at any time t depends only on the input at that same time t. Otherwise the system has memory
- Causality: A system is causal if the output depends on the input for t < t0
	- Output depends on only the past and present input values
- Stability: System is stable if for any bounded input x (| x(t) | <= k1 or | x[n] | <= k1), the output y is also bounded (| y(t) | <= k2 or | y[n] <= k2)
	- Unstable system could be something like that bridge that swayed so much that it failed
- Invertibility: If distinct inputs lead to distinct outputs. If invertible, an "inverse system" exists
- Example:
	- ![[Pasted image 20240830211313.png]]
	- It is memoryless bc it only depends on the current input, no x[n-1], etc.
	- Not invertible bc an input and its opposite sign will gain the same result
	- For example, x = -2 will be the same as x = 2
## Linear, Time-Invariant Systems
- A system is linear if it satisfies the following property: ![[Pasted image 20240830211720.png]]
- Scaling: ![[Pasted image 20240830214729.png]]
- Superposition: ![[Pasted image 20240830214740.png]]
- ![[Pasted image 20240830214820.png]]
- A system is time-invariant if it satisfies the following property: ![[Pasted image 20240830214949.png]]
- ![[Pasted image 20240830215026.png]]
- LTI systems are of great importance in systems theory and will be treated in detail in module 2
- Example:
	- ![[Pasted image 20240830215124.png]]
	- Not linear in scaling or superposition:
		- Scaling: ![[Pasted image 20240830215251.png]]
		- Superposition: ![[Pasted image 20240830215340.png]]
- Example 2: 
	- ![[Pasted image 20240830215354.png]]
	- Also clearly not time-invariant bc a delay would still get the same output
	- Not linear:
		- ![[Pasted image 20240830222355.png]]
		- ![[Pasted image 20240830222437.png]]