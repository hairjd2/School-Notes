# Chapter 7: First Order (RC, RL) Circuits
## 1. Source-free response of RC circuit
- This means after switching, the circuit contains no independent voltage source
- It is a 1st order differential equation of homogeneous type, which means that the differential equation is equal to 0
- ![[Pasted image 20220315103922.png]]
- $\tau = RC$ --- time constant of RC circuit
- $v(t) = v(0^+)e^{-\frac{t}{\tau}}$
- $v(0^+)$ --- initial capacitor voltage
- It is the capacitor discharging process the current comes from releasing of the energy stored in the capacitor
- Physical (ground-zero) initial condition is the capacitor voltage right before switching at $t = 0^-$
	- $v(0^-)$
- Mathematical initial condition $v(0^+)$ is from the continuity of capacitor voltage
	- $v(0^+) = v(0^-)$ by capacitor voltage continuity
- Capacitor energy
	- $w_c(0^+) = \frac{1}{2}Cv^2(0^+)$
	- $w_C(t) = \frac{1}{2}Cv_C^2 = \frac{1}{2}Cv^2(0^+)e^{-\frac{2t}{\tau}} = w_C(0^+)e^{-\frac{2t}{\tau}}$
- Power Dissipated by resistor
	- $p_R = vi_R = \frac{v^2}{R} = \frac{v^2(0^+)}{R}e^{-\frac{2t}{\tau}}$
	- Note: $i_C = -i_R$
	- $p_C = vi_C = -p_R$
## 2. Source-free response of RL circuit
- Similar to the RC circuit, it is after switching to a circuit with no independent current source
- It is also a 1st order differential equation of homogeneous type
- ![[Pasted image 20220315110505.png]]
- $\tau \equiv \frac{L}{R}$ --- time constant of RL circuit
- $i(0^+)$ --- initial inductor current
- It is the discharging process. The current comes from releasing of the energy stored in the inductor
## 3. Step response of RC and RL circuits
### RC Circuit
- ![[Pasted image 20220315110536.png]]
- 1st order differential equation of non-homogeneous type
- $\frac{dv}{dt} + \frac{v}{RC} = \frac{V_s}{RC}$
### RL Circuit
- ![[Pasted image 20220315110957.png]]
- 1st order differential equation of non-homogeneous type
- $\frac{di}{dt} + \frac{R}{L}i = \frac{V_s}{L}$
## 4. General Response of RC and RL circuits
- 1st order differential equation of non-homogeneous type
## Unit Step Functions
- u(t) is normal step function
- u(t-t<sub>0</sub>) means a shift to the right
- u(t+t<sub>0</sub>) means a shift to the left
- u(-t+t<sub>0</sub>) means a flipped graph and a shift to the right 