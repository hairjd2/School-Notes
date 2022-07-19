# Chapter 8: Second-Order (RLC) Circuits
## 1. Source Free Response
### - Series RLC Circuit
- ![[Pasted image 20220329102832.png]]
- KVL: v<sub>R</sub> + v<sub>L</sub> + v<sub>C</sub> = 0
- Apply Resistor and inductor device laws
	- $Ri+L\frac{di}{dt}+v_C$
- $\frac{d}{dt}$ equation one more time
	-   $R\frac{di}{dt}+L\frac{d^2i}{dt^2}+\frac{dv_C}{dt}$
- Apply capacitor device law
	- $i = C\frac{dv_C}{dt}$
	- $\frac{d^2i}{dt^2}+\frac{R}{L}\frac{di}{dt}+\frac{i}{LC}=0$
- Similar to parallel RLC circuit
	- $\frac{d^2v}{dt^2}+\frac{1}{RC}\frac{dv}{dt}+\frac{v}{LC}=0$
- Serial RLC: $\alpha = \frac{R}{2L}; \omega_0=\frac{1}{\sqrt{LC}}$
- Parallel RLC: $\alpha = \frac{R}{2RC}; \omega_0=\frac{1}{\sqrt{LC}}$
### Three types of response
1. Over-damped case ($\alpha > \omega_0$)
2. Under-damped case ($\alpha < \omega_0$)
3. Critically-damped case ($\alpha = \omega_0$)
## 2. Step Response
### Series RLC Circuit