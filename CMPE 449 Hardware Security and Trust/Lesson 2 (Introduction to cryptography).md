- By convention, plaintext is in uppercase and ciphertext is in lowercase
- P = D(C) = D(E(P))
	- E: encryption algo
	- D: decryption algo
	- C: ciphertext
	- P: plaintext
# Crypto System with keys
- C = E(K<sub>E</sub>, P)
- P = D(K<sub>D</sub>, C)
- Keyless systems exist, like hashing algos, usually for one way encryption
- Symmetric cryptosystems are $K_E=K_D$
- Asymmetric cryptosystems are $K_E \ne K_D$
	- Public and private key system
# Cryptanalysis
- Break a single msg
- Recognize patterns in encrypted msgs
- Infer meaning w/o breaking encryption
- Deduce the key
- Find vulnerabilities in the implementation
- Find a general weakness in an encryption algo
## Info used
- Intercepted msgs
- Known encrypted algos
- Intercepted plaintext
- Data known or suspected to be ciphertext
- Properties of natural languages
- Properties of computer systems
## Breakable Encryption
- Theoretically it is possible to device an unbreakable cryptosystem
- Practical cryptosystems almost are always breakable
- Trick is to make breaking the system hard enough for the intruder
# Ciphers
## Substitution
- Letters of P replaced with other letters by E
- Caesar Cipher
- Vigenere Tableaux (First lab)
### Attacks
- Exhaustive search
	- Only have 26 possible keys
	- Easy to try all possible keys
- Statistical Analysis
	- Compare to so called 1-gram (unigram) model of English
	- Shows frequency of single chars in English
	- The longer the C, more effective statistical analysis would be
	- ![[Pasted image 20240206164044.png]]
- Statistical Analysis
	1. Compute frequency of each letter c in ciphertext
	2. Apply the 1-gram model of English
		1. phi $\varphi(i)$ 
	3. Correlate $\varphi(i)$ for $0\le i\le 25$
	4. Find most probable keys
### Vigenere Tableaux
- ![[Pasted image 20240206165542.png]]
- ![[Pasted image 20240206170131.png]]
## Transposition (permutation) ciphers
- Order of letters in P rearranged by E
- Columnar Transposition
	- Transpose the string into x number of columns
	- ![[Pasted image 20240206170328.png]]
- Rail-Fence Cipher
	- Transpose into x number of rows (railes)
	- ![[Pasted image 20240206170417.png]]
## Product ciphers
- Combine two or more ciphers to enhance the security of the cryptosystem
- a.k.a. combination ciphers
- Example: two-block product cipher
	- $E_2(E_1(P, K_{E1}), K_{E2})$
- This may not be necessarily stronger than its individual components used separately
## What makes a good Cipher
- Depends on the intended application
- Commercial Principles of Sound Encryption Systems
	- Sound mathematics
	- Verified by expert analysis
	- Stood the test of time
- Examples of popular commercial encryption
	- DES (Data Encryption Standard)
	- RSA (Rivest-Shamir-Adelman)
	- AES (Advanced Encryption Standard)
## Stream Ciphers
- 1 char from P -> 1 char for C
- Basically the plaintext and ciphertext will be the same size
- 