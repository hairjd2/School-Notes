# TODO:
- Hw1
- Project 1
# Key Relationships
- $\cap$
- $Pr[A \cup B]$
- ==**Independence is not the same as mutual exclusivity**==
- ==**Events aren't numbers, probability is**==
# Graphical Analysis
- Multiple elements maybe connected in series or parallel
	- A = "communicate by link A"
	- B = "communicate by link B"
	- $Pr[comm] = Pr[AB] = Pr[A]Pr[B]$
	- $Pr[!comm] = 1 - Pr[A]Pr[B]$
	- $Pr[communicate] = Pr[A+B] = Pr[A] + Pr[B] - Pr[A]Pr[B]  \leq Pr[A] + Pr[B]$
## Communication Example
- A,B,C,D = "communications takes place over appropriate link"
- Let $q=(1-p)=Pr[A]=Pr[B]=Pr[C]=Pr[D]$
- Assuming A,B,C,D are independent
# Conditional Probabilities
- We've been asking probabilities as if we know nothing
- Let $A_1$, $A_2 \in S$. The conditional probability of $A_1$ knowing that $A_2$ has occurred is defined by the relation
- $Pr[A_1 | A_2] = \frac{Pr[A_1A_2]}{Pr[A_2]}$
- Because $0 < Pr[A_2] \leq 1, Pr[A_1 | A_2] \geq Pr[A_1A_2]$
- $0 < Pr[A_2]$ because we know $A_2$ has occurred, and therefore, $Pr[A_2] \neq0$
- $Pr[A_1A_2] = Pr[A_1 | A_2]Pr[A_1]=Pr[A_2|A_1]Pr[A_1]$
- $Pr[A_1|A_2] = \frac{Pr[A_1A_2]}{Pr[A_1]}=\frac{Pr[A_1|A_2]Pr[A_2]}{Pr[A_1]}$
- For $A_1->A_n$ a partition of S, $B \in S$: $\sum{j=1}{\inf}$
- 