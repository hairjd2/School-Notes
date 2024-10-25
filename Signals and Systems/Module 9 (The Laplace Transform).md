# Definition of the Laplace Transform
![[Pasted image 20241019130053.png]]
- The complex variable is written in cartesian form
- Talk about the transform in the s-plane (imaginary plane)
- ![[Pasted image 20241019130303.png]]
## Example 1
- ![[Pasted image 20241019130756.png]]
- Make a = 1
	- ![[Pasted image 20241019130833.png]]
- ![[Pasted image 20241019131033.png]]
- ![[Pasted image 20241019131257.png]]
- ![[Pasted image 20241019131316.png]]
- ![[Pasted image 20241019131336.png]]
- This is called the Region of Convergence
	- The region in the s-plane in where the transform converges
- Pole s = -a
## Example 2
- ![[Pasted image 20241019131537.png]]
- ![[Pasted image 20241019132159.png]]
- ![[Pasted image 20241019132221.png]]
- ![[Pasted image 20241019132308.png]]
- Must define the functional form AND the ROC of the laplace transform
## Examples
- ![[Pasted image 20241019132453.png]]
- Shows the ROC of each function in time
# Region of Convergence (ROC) of the Laplace Transform
- ![[Pasted image 20241019135001.png]]
- ![[Pasted image 20241019135157.png]]
	- Acts as a damping factor
- ![[Pasted image 20241019135234.png]]
# Properties of the Laplace Transform
- ![[Pasted image 20241019135407.png]]
- Linearity, similar to what we've seen
	- However, now we are concerned with ROC
	- The sum of the Laplace Transforms leads to the intersection of the two ROCs
- Convolution is the same as for FTs, however the ROC is also the intersection
- Differentiation and Integration important for LTI systems analysis
# Poles and Zeros
- ![[Pasted image 20241019140538.png]]
- They are typically rational functions because: ![[Pasted image 20241019140918.png]]
- In the examples we've seen, the pole sat right outside of the ROC, where the ROC was either to the left or the right of it
- We'll see that the location of the poles for a LTI system is important for determining stability
# Inverse Laplace Transform
- Inverse Laplace Transform via Partial Fraction Expansion: ![[Pasted image 20241019143330.png]]
- ![[Pasted image 20241019143538.png]]
	- Also often called residues
## Example #1
- ![[Pasted image 20241019143754.png]]
- Start by factoring it out
- ![[Pasted image 20241020150826.png]]
- ![[Pasted image 20241020150833.png]]
- ![[Pasted image 20241020151624.png]]
- ![[Pasted image 20241020151646.png]]
- ![[Pasted image 20241020152405.png]]
- Can use matlab function "residue"
## Example 2
- ![[Pasted image 20241020202450.png]]
- ![[Pasted image 20241020202631.png]]
- ![[Pasted image 20241020202757.png]]
- ![[Pasted image 20241020202456.png]]
- Signal is right-sided when the ROC is to the right of all of the poles
- (a) Re(s) > 2
- ![[Pasted image 20241020203009.png]]
- So this is divergent
- (b): ![[Pasted image 20241020203245.png]]
# LTI Systems Analysis Using the Laplace Transform
- ![[Pasted image 20241020211457.png]]
- Causal: The impulse response is 0 for negative time
- Stability: must be absolutely integratable
# Differential Equations and the Laplace Transform
- ![[Pasted image 20241020212032.png]]
- ![[Pasted image 20241020212206.png]]
- ![[Pasted image 20241020212327.png]]
- transfer function to zero pole: tf2zp
- ![[Pasted image 20241020212449.png]]
- ![[Pasted image 20241020212713.png]]
- ![[Pasted image 20241020212827.png]]
- Laplace transform frequency response: freqs
- `freqs(b,a)`:![[Pasted image 20241020212910.png]]
- ![[Pasted image 20241020213121.png]]