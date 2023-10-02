# Capacitance
- Approximate channel as connected to source
- $C_{gs}=\epsilon_{ox}\frac{WL}{t_{ox}}=C_{ox}WL=C_{permicron}W$
- $C_{permicron}$ is typically $2f\frac{F}{\mu m}$
- Gate capacitance creates channel charge necessary for operation
# Diffusion Cap
- $C_{sb}$ and $C_{db}$ is undesirable, called parasitic capacitance
- ![[Pasted image 20230927131928.png]]
- $C_j$ is the junction capacitance per unit area
- $C_j=C_{j0}(1+\frac{V_{sb}}{\phi_{0}})^{-M_{j}}$
# Side-wall Cap
- Side-wall Capacitance: Formed by the source region with doping $N_D$ and the $p^+$channel-stop implant with doping $N_A^+$
- $C_{sw}=C^{'}_{jsw}x_j(W + 2 * L_S)$
- $C_{diff}=C_{bottom}+C_{sw}=C_j*AREA+C_{jsw}*PERIMETER$
- $C_{diff}=C_jL_SW+C_{jsw}(2L_S+W)$
# Gate Overlap Cap
- ![[Pasted image 20230927132955.png]]
- Lateral diffusion: source and drain diffusion extend under the oxide by an amount $x_d$. The effective channel length ($L_{eff}$) is less than the **drawn length** L by $2*x_d$
- $C_{gsO}=C_{gdO}=C_{ox}x_dW=C_{O}W$
# Source Drain Resistance
- Scaling causes junctions to be **shallower** and contact openings to be **smaller**
- This increases the parasitic resistance in series with the source and drain regions
- ![[Pasted image 20230927134754.png]]
- 