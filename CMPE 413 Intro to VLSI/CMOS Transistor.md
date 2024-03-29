- So far, we treated MOSFETs as ideal switches
- On transistor passes finite amount of current
	- Depends on terminal voltages
	- Need to derive I-V characteristics
- **gate** **source** and **drain** have capacitance
	- ![[Pasted image 20230920132723.png]]
- Positive/negative voltage applied to the gate (with respect to substrate) enhances the number of electrons/holes in the channel and increases conductivity between source and drain
- $V_t$ defines the voltage at which a MOS transistor begins to conduct
- For voltages less than $V_t$, the channel is cut off
- ![[Pasted image 20230920133006.png]]
- Although threshold voltage is given, its not just a magic number
# Modes of Operation
- Depends on terminal voltages
	- $V_{gs} = V_g - V_s$
	- $V_{gd} = V_g - V_d$
	- $V_ds = V_d - V_s = V_{gs} - V_{gd}$
- **Rule of thumb**: source is always lower voltage for NMOS
- Opposite for PMOS
## Three modes (very important)
- Cutoff
	- When $V_g < V_t$ or $V_{gs}$
	- $I_{ds} = 0$
- Linear or Triode
	- Channel is formed and extends from the source to the drain
	- Current flow from drain to source (electrons)
	- $I_{ds}$ increases with $V_{ds}$
	- Similar to linear resistor
	- ![[Pasted image 20230920134711.png]]
	- ![[Pasted image 20230920134721.png]]
	- 
- Saturation
	- Channel is pinched off near the drain
	- $I_{ds}$ independent of $V_{ds}$. $I_{ds}$ is a function of $V_{gs}$ only
	- We refer to it as current saturates
	- Similar to a current source
	- ![[Pasted image 20230920135223.png]]
# MOS I-V Characteristics
- Parameters that affect the magnitude of $I_{ds}$
	- Distance between s and d
	- Channel width
	- Threshold voltage
	- Thickness of the gate oxide layer
	- Dielectric constant
	- The carrier mobility
- Summary of normal conduction characteristics
	- Cut-off: accumulation, current between drain and source is essentially 0
	- Non-saturated: weak inversion, current dependent on both $V_{gs}$ and $V_{ds}$
	- Saturated: strong inversion: $I_{ds}$ is ideally independent of $V_{ds}$
- ![[Pasted image 20230925132336.png]]
- 
## Linear
- $I=\frac{dQ}{dt}=\frac{Q}{t}=?$
- $I_{ds}=\frac{CV}{t}$
- $C = \epsilon_{ox}(\frac{A}{d})=\epsilon_{ox}(\frac{WL}{t_{ox}})=(\frac{\epsilon_{ox}}{t_{ox}})WL=C_{ox}WL$
- $V=(V_{gc}-V_{t})$
- $V_C=\frac{V_s+V_d}{2}=\frac{2V_s+(V_d-V_s)}{2}=V_s+\frac{V_{ds}}{2}$
## Mobility
- All dopings and voltages reversed by PMOS
	- Mobility $\mu_p$ is determined by holes
	- Typically it is 2-3 times lower than that of electrons
- ![[Pasted image 20230925133219.png]]
## Threshold Voltage
- $V_t$ is also an important parameter
- Most are related to material properties
- Usually determined at time of fab
- Parameters include
	- Gate conductor material
	- Gate insulation material
	- The thickness of gate material
	- Channel doping concentration
- Also dependent on
	- $V_{sb}$, the voltage between source and substrate
	- Temperature
- ![[Pasted image 20230925135243.png]]
### Body Effect
- ![[Pasted image 20230925135312.png]]
- The substrate is usually held at 0 for digital circuits
- Sources of n-channel devices, for example, are also held at zero, except in cases of series connections, like:
- ![[Pasted image 20230925135428.png]]
- $P=IV=\alpha C_LV_{DD}^2f$
- 