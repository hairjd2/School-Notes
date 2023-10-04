- DC Response: $V_{out}$ vs. $V_{in}$ for a gate
- ![[Pasted image 20230927140814.png]]
- For inverter: ![[Pasted image 20231002130514.png]]
- Bottom curve very important for exam
# Beta-Ratios
- $\beta=\mu C_{ox}(\frac{W}{L})$
- Get ratio that gives you rise and fall time of each transistor to be the same
- If $\beta_p \neq \beta_n$, switching point will move from $V_{DD}/2$
- Called **skewed** gate
# Noise Margin
- ![[Pasted image 20231002135122.png]]
- ![[Pasted image 20231002135747.png]]
# Pseudo-NMOS Inverter
- ![[Pasted image 20231002141118.png]]
- Removes the need for Pull-up network logic
# Functionality and Robustness
- Nothing "goes into" a logic gate, just has a input voltage
## Directivity
- Requires gate to be unidirectional
- Otherwise noise is generated on gate inputs
## Fan-in and Fan-out
- Increasing the fan-out of a gate can affect its static logic output levels
- Thats why we had a fan out of 4
- ![[Pasted image 20231004131039.png]]
- $gain=\frac{\Delta V_{out}}{\Delta V_{in}}=\frac{g_{m}^{in}}{g_{m}^{out}}=g_{m}^{in}*R_{out}$
# Performance
- What is performance or speed
- Performance expressed by clock period and clock frequency
- Think about 3 things:
	1. Propogation delay through the logic
	2. Time to get data in and out of the registers
	3. Uncertainty in the clock arrival times (clock skew)
- $T_p=t_s+t_{C-Q}+t_p+t_{skew}+t_{jitter}$
- ![[Pasted image 20231004133112.png]]
- Can use a ring oscillator to measure performance:
- ![[Pasted image 20231004133325.png]]
- Ring oscillators are **de-facto** standard circuit for unbiased delay measurements
- Period T of the oscillation: $T=2*t_p*N$ -- N is # of inverters in the chain
- The factor of 2 indicates that a fully cycle consists of both a HL and LH transition
- This equation holds true only for: $2Nt_p> >t_f+t_r$
- Circuit below used to model digital circuit
- ![[Pasted image 20231004134648.png]]
- $v_{out}(t)=(1-e^{-t/\tau})V$
## Power Consumption
- Determines how much energy is consumed during an operation and how much heat is disspated
- Affects important design decisions:
	- Power-supply capacity
	- Battery lifetime
	- Supply-line sizing
	- Packaging
	- Cooling requirements
- Peak power is import for supply-line sizing
- Average power dissipation is important for cooling and battery life
- $P_{peak}=i_{peak}V_{supply}=max[p(t)]$
- $P_{av}=\frac{1}{T}\int_{0}^{T}p(t)dt=\frac{V_{supply}}{T}\int_{0}^{T}i_{supply}(t)dt$
- $p(t)$ is instantaneous power
- $i_{supply}$ is the current drawn from the supply voltage over the time interval t
- PPA (Power Performance and Area)
## Propagation Delay
- Propagation delay and power consumption are related
- If faster, it uses more power, and vice versa