# Discrete-Time Convolution
- Recall: ![[Pasted image 20240901133301.png]]
	- This shows the "stemming" of each value of the DT signal
	- It defines the superposition of the signal
- ![[Pasted image 20240901133325.png]]
- that h[n] = H{\delta[n]} is called the system impulse response
- You can find any output signal by any delay k just by knowing the system impulse response
- Convolution denoted by \*, like $y[n]=x[n]*h[n]$
- ![[Pasted image 20240901161555.png]]
## Convolution Computational Approaches
### Sum of Weighted and Shifted Impulse Responses
- Compute the convolution between the following two sequences:
- ![[Pasted image 20240902180624.png]]
- ![[Pasted image 20240902190902.png]]
### Term-by-Term
- Same example as above
- ![[Pasted image 20240902191042.png]]
- ![[Pasted image 20240902194955.png]]
- ![[Pasted image 20240902195007.png]]
## Flip and Slide
1. Time reverse the impulse response and shift by n0 samples to form h[n0-k], which is a function of k with parameter n0
	- ![[Pasted image 20240902202621.png]]
2. Multiply term-by-term x[k] and h[n0-k], which is a function of k
	- ![[Pasted image 20240902202735.png]]
	- ![[Pasted image 20240902202750.png]]
3. Sum the product sequence x[k]h[n0-k] to yield the single output sample y[n0]
	- ![[Pasted image 20240902202837.png]]
4. Repeat to find other output samples y[n]
## Convolution and MATLAB
### Handy Rules of Thumb for DT Convolution
- If x[n] has length M and h[n] has length N, then y[n]=x[n]\*h[n] has length M+N+1
- The starting index of y[n] is the sum of the starting indices of x[n] and h[n]
- The ending index of y[n] is the sum of the ending indices of x[n] and h[n]
# Continuous-Time Convolution
- ![[Pasted image 20240902210156.png]]
- If this signal is input to a LTI system H, then
	- ![[Pasted image 20240902210216.png]]
## Procedure for Calculating CT Convolution
1. Time reverse the impulse response and shift by t to form h[t-tau], which is a function of tau with parameter t
2. Multiply term-by-term x[tau] and h[t-tau], which are both functions of tau
3. Integrate the product x(tau)h(t-tau) to yield the single output signal value y(t)
4. Shift h(t-tau) to find other output values y(t)
## Convolution Example #1
- ![[Pasted image 20240902233048.png]]
- ![[Pasted image 20240902233249.png]]
- ![[Pasted image 20240902233258.png]]
- ![[Pasted image 20240902233626.png]]
- ![[Pasted image 20240902233742.png]]
- ![[Pasted image 20240902233845.png]]
## Convolution Example #2
- ![[Pasted image 20240902233925.png]]
- ![[Pasted image 20240902234240.png]]
- ![[Pasted image 20240902234300.png]]
- ![[Pasted image 20240902234321.png]]
# Properties of LTI Systems
## Handy Rules of Thumb for DT Convolution
- If x[n] has length M and h[n] has length N, then y[n]=x[n]\*h[n] has length M+N+1
- The starting index of y[n] is the sum of the starting indices of x[n] and h[n]
- The ending index of y[n] is the sum of the ending indices of x[n] and h[n]
## Handy Rules of Thumb for CT Convolution
- If x(t) has duration L and h(t) has duration M, then y(t)=x(t)\*h(t) has duration L+M
- Starting time and ending time of y(t) is the sum of the starting and ending times of x(t) and h(t)
## Properties of Convolution
- Commutative Property:
	- ![[Pasted image 20240903233123.png]]
	- ![[Pasted image 20240903233127.png]]
	- Helps with when you choose to use the easier signal
- Associative (series or cascade systems)
	- ![[Pasted image 20240903233313.png]]
	- ![[Pasted image 20240903233318.png]]
	- ![[Pasted image 20240903233426.png]]
- Distributive (parallel systems)
	- ![[Pasted image 20240903233608.png]]
	- ![[Pasted image 20240903233613.png]]
	- ![[Pasted image 20240903233721.png]]
## Memoryless
- A system is memoryless if the output at any time t (or n) depends on only the input at that same time t (or n). Otherwise, the system has **memory**
- ![[Pasted image 20240903233917.png]]
- ![[Pasted image 20240903233926.png]]
- Memoryless LTI systems are just scaled systems of the input
## Causality
- A system is causal if the output y(t0) (y[n0]) depends only on the input x(t0) for t <= t0 (x[n0] for n <= n0)
- ![[Pasted image 20240903234656.png]]
- ![[Pasted image 20240903234706.png]]
## Stability
- A system is stable if for any bounded input x (| x(t) | <= k1 or | x[n] | <= k1), the output y is also bounded (| y(t) | <= k1 or | y[n] | <= k1)
- If you take the absolute value of the input signal that is bounded by some upper bound which should lead to an output upper bound
- Stable LTI CT systems must have an absolutely integrable impulse response
- ![[Pasted image 20240903235133.png]]
- ![[Pasted image 20240903235156.png]]
- The equivalent for a DT system is that its absolutely summable
## Differential and Difference Equations (Alternative Representations)
- CT LTI systems may also be described by linear, constant-coefficient diff eqs
	- ![[Pasted image 20240904000055.png]]
	- ![[Pasted image 20240904000158.png]]
- DT LTI Systems may also be described by linear, constant-coefficient diff eqs:
	- ![[Pasted image 20240904000406.png]]
	- ![[Pasted image 20240904000618.png]]
	- Has what's called feedback
	- Special Case: N = 0 ![[Pasted image 20240904000717.png]]
		- Such systems are knwon as finite impulse response (FIR)
		- Otherwise, systems are infinite impulse response (IIR)
		- Example Three sample moving averager: ![[Pasted image 20240904000800.png]]
			- ![[Pasted image 20240904000917.png]]
## Examples of LTI System Properties
### Example 1
- Three-sample moving averager
- ![[Pasted image 20240904211851.png]]
- What is the system's impulse response?
	- ![[Pasted image 20240904212009.png]]
	- ![[Pasted image 20240904212015.png]]
	- ![[Pasted image 20240904212022.png]]
- Is the system memoryless
	- Has memory since it has non-zero values at other intervals other than the origin
	- h[n]/=ksigma[n]
- Causal bc h[n]=0, n<0
- Stable
	- ![[Pasted image 20240904212211.png]]
	- So it is stable
- This is FIR (every FIR system is stable)
### Example 2
- DT System describing a savings account
- ![[Pasted image 20240904212329.png]]
- Impulse response
	- ![[Pasted image 20240904212546.png]]
	- ![[Pasted image 20240904212533.png]]
	- ![[Pasted image 20240904212553.png]]
- This would be IIR therefore
- Memoryless?
	- Has memory, h[n]/=k sigma[n]
- Causal?
	- Causal, h[n]=0, n<0
- Stable?
	- ![[Pasted image 20240904212700.png]]
	- Unstable