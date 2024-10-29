# Intro to z-Transform
- ![[Pasted image 20241027225549.png]]
- that omega angle can be seen as the DT frequency we saw in FT
# Examples
## Example 1
- ![[Pasted image 20241027230217.png]]
- ![[Pasted image 20241027230241.png]]
- ![[Pasted image 20241027230326.png]]
- ![[Pasted image 20241027230339.png]]
## Example 2
- ![[Pasted image 20241027230436.png]]
- ![[Pasted image 20241027230441.png]]
- ![[Pasted image 20241027230627.png]]
	- ![[Pasted image 20241027230639.png]]
- ![[Pasted image 20241027230657.png]]
## Example 3
- ![[Pasted image 20241027230841.png]]
- ![[Pasted image 20241027230851.png]]
- Now need to limit from -inf to 0
- ![[Pasted image 20241027231114.png]]
- ![[Pasted image 20241027231127.png]]
- ![[Pasted image 20241027231218.png]]
# Region of Convergence
- ![[Pasted image 20241027231423.png]]
- ![[Pasted image 20241027231516.png]]
# Properties of the z-Transform
- ![[Pasted image 20241027231601.png]]
- $z=e^{j\omega}$ for time shift
- ![[Pasted image 20241027231833.png]]
- z-transforms are rational functions
- ![[Pasted image 20241027231918.png]]
# Inverse z-Transform
- ![[Pasted image 20241028190603.png]]
- Assuming that the rational function making the z-transform (proper rational function) has distinct and N > M
## Example 1
- ![[Pasted image 20241028191009.png]]
- ![[Pasted image 20241028191253.png]]
- ![[Pasted image 20241028191322.png]]
- ![[Pasted image 20241028191654.png]]
- 2 poles has three DT signals associated
# MATLAB and the z-Transform
- residuez: z-transform partial fraction expansion
- ![[Pasted image 20241028192134.png]]
## Example 2
- ![[Pasted image 20241028192159.png]]
- ![[Pasted image 20241028192400.png]]
- ![[Pasted image 20241028192540.png]]
- ![[Pasted image 20241028192551.png]]
- ![[Pasted image 20241028192601.png]]
- ![[Pasted image 20241028192635.png]]
# LTI Systems Analysis with the z-Transform
- ![[Pasted image 20241028192758.png]]
# Difference Equations and the z-Transform
- ![[Pasted image 20241028193205.png]]
- ![[Pasted image 20241028202514.png]]
- Used `zplane(b,a)` to find the poles
- ![[Pasted image 20241028202909.png]]
- ![[Pasted image 20241028203135.png]]
- `freqz(b,a)` to plot the frequency response of z-transform
- ![[Pasted image 20241028203807.png]]
- Using the residues
- Lets you compute the impulse response values `impz(b,a,21)` will generate 21 values