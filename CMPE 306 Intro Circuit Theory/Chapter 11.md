# Sinusoidal Power Definitions
- $v(t)=V_mcos(\omega t+\theta _V)=V_mcos(\omega t+\theta _V-\theta _i)$
- $i(t)=I_mcos(\omega t+\theta _i)=I_mcose(\omega t)$
## Instantaneous Power
- $p(t) = v(t)i(t)$
- $p(t) = V_mI_mcos(\omega t+\theta _V-\theta _i)cos(\omega t)$
- $p(t)=-\frac{1}{2}V_mI_msin(\theta _V-\theta _i)sin(2\omega t)$
## Average Power
- $P=\frac{1}{T}\int_{0}^{T}p(t)dt=\frac{1}{2}V_mI_mcos(\theta _V-\theta _i)$
### 1. Pure Resistor ($\theta _V=\theta _i$)
- $p_R(t) = P_R+P_Rcos(2\omega t)$
- $p_R(t)\ge0$ --- always dissipate power
- $P_R=\frac{1}{2}V_mI_m$ (non-zero average power)
### 2. Pure inductor ($\theta _V=\theta _i+90^\circ$)
- $p_L(t)=-\frac{1}{2}V_mI_msin(2\omega t)
- When $p_L(t)>0$ --- half cycle under charging
- When $p_L(t)<0$ --- half cycle under discharging
- $P_L=0$ (zero average power)
### 3. Pure Capacitor ($\theta _V=\theta _i+90^\circ$)
