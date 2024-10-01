# Definition of the DTFT
- ![[Pasted image 20240929231412.png]]
- Also use integration for DTFT like we do in CTFT
- The second implementation is not the best for computer calculation since its an infinite sum
- Gonna look at trying to make that second expression implementable on a computer
- ![[Pasted image 20240929232023.png]]
## DTFT of One-Sided Exponential Signal
- ![[Pasted image 20240929232424.png]]
- ![[Pasted image 20240929232510.png]]
- ![[Pasted image 20240929232845.png]]
## Inverse DTFT Example
- Euler's inverse identity: ![[Pasted image 20240929233237.png]]
- ![[Pasted image 20240929233304.png]]
- sinc function like seen in CTFT
- ![[Pasted image 20240929233524.png]]
- ![[Pasted image 20240929233536.png]]
- Problem at n=0 bc sin(0)=0 and 0/0 is not doable
- ![[Pasted image 20240929233753.png]]
## Finding the DTFT of Finite Length Signals
- ![[Pasted image 20240929234156.png]]
- Factor out the half angle
- ![[Pasted image 20240929234344.png]]
- Bc you have a e^j and e^-j gives you a ratio of sin's
- ![[Pasted image 20240929234359.png]]
### "Computing" the DTFT for Finite Length Sequences
- Relationship with finding DTFS
- ![[Pasted image 20240929234614.png]]
- 