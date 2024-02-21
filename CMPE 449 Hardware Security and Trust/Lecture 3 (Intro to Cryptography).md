# Block Cipher
- Cipher with a fixed size
- Needs to wait for the whole message to be sent
- Block size = "o(message length)"
	- Because R must wait for "almost" the entire C before R can decode some characters near beginning of P
## Primitives
- Both operations by themselves cannot provide security. The idea is to concatenate confusion and diffusion elements to build so called product ciphers.
### Confusion
- An encryption operation where the relationship between key and ciphertext
- Hides the relationship between the key and ciphertext
- each bit of the ciphertext should depend on several parts of the key
### Diffusion
- An encryption where the influence of one plaintext symbol is spread over many ciphertext symbols with the goal of hiding statistical properties of the plaintext
- When changing a single bit of the plaintext, at least half of the bits in the ciphertext should change
# Pros and Cons
## Stream Ciphers
- Pros
	- Low delay for decoding individual symbols
	- Low error propagation
- Cons
	- Low diffusion
	- Susceptibility to malicious insertion/modification
## Block ciphers
- Pros
	- High diffusion
	- Immune to insertion
- Cons
	- High delay for decoding individual chars
	- High error propagation
# Keys
## Symmetric Encryption
- Keys are the same for encryption and decryption
- You would need $(\frac{n}{2}) = \frac{n!}{2!(n-2)!}$
- So for when n=8, you would need 26 keys
## Asymmetric Encryption
- The encryption and decryption keys
- You will only need 16 for 8 people, 2 per person
- They will use the public key to encrypt in which the receiver can only decrypt
- So not even the sender can decrypt the ciphertext even if they encrypted it
# DES (Data Encryption Standard)
- Block cipher
	- Product cipher
	- 16 rounds (iterations) on the input bits
		- Substitutions (for confusion) and permutations (for diffusion)
	- Each round with a *round* ley
- 72 quadrillion or more possible encryption keys that can be used
## Features
- Block size: 64 bits
- Key size: 56 bits (in reality, 64 bits but 8 are used as parity-check bits)
- Number of rounds: 16
- Will be a question on slide 22
## Basic Structure
- Input is 64 bits (need to be padded if too small)
### Input Permutaion
### f Function
- Passes in current right side and key
- First expands the right side (32 bits) into 48 bits by repeating every 4 bits
- Then sent to an s box
#### SBox
- ![[Pasted image 20240213163130.png]]
## Key Schedule
- DES key length: 64 bits
- In each byte, the 8th bit is for parity
- Goes through the same permutation as the plaintext
## Problems
- Key length is fixed (=56)
- 2^56 keys ~ 10^15 keys
- "Becoming" too short for faster computers
- Design decisions not public
	- suspected of having backdoors
	- Speculation: To facilitate government access?
## Multi-DES
- Uses multiple factors of DES, using a new key each time
- Isn't very effective for double-DES since an attack can parallelly see what keys would match the encryption of P with k1 and the decryption of C with k2
- Triple DES:
	- ![[Pasted image 20240213165257.png]]
- This is strong even for today's computer
- Is not insecure... yet
- But a search for a new encryption standard had begun in 1995
# AES (Advanced Encryption Standard)
## Contest
- NIST calls for proposal for encryption algorithm
	- Must be:
		- unclass code
		- publicly disclosed
		- royalty free worldwide
		- symmetric block cipher for 128-bit blocks
		- Usable with keys of 128, 192, and 256 bits
- 1998 - 15 algorithms selected
- 1999 - 5 finalists
	- MARS by IBM
	- RC6 by RSA Labs
	- Rijndael
	- Serpent 
	- Twofish
- Winner was Rjindael, and adopted by USG as Federal Info Processing Standard 197 (FIPS 197)
## Features
- Block size is 128 bits
- Key can be 128 (10 rounds), 192 (12 rounds) or 256 bits ( 14 rounds)
- Basic operations for a round
	- Substitution - byte level (confusion)
	- Shift row (transposition) - depends on key length (diffusion)
	- Mix columns - LSH and XOR (confusion + diffusion)
	- Add subkey - XOR used (confusion)
- byte-oriented cipher
- State A (the 128 bit data path) can be arranged in 4x4 matrix
## Algorithm
- For the 0th round, its just xored with the key
- For the other rounds
	1. S-box
	2. shift row
	3. mix column
		- The matrix you multiply by are found from GF(2^8)
	4. key $\oplus$
		- Each round key is 4 bytes of the 16 bytes
- $x^8+x^4+x^3+x+1$
- 
# Public Key Crypto
## Characteristics
- PKE requirements:
	- It must be computationally easy to encipher or decipher a message given the appropriate key
	- It must be computationally infeasible to derive k<sub>priv</sub> from k<sub>pub</sub>
	- It must be computationally infeasible to determine k<sub>priv</sub> from a chosen plaintext attack
- Key pair characteristics
	- One key is inverse of the other key of the pair
	- One of the keys can be public since each key does only half of E "+" D
## RSA Example
- Alice picks two primes *p*, *q* and computes $N=p*q$
- Alice chooses exponent *e* which satisfies: $gcd(e, \phi(n))=1; gcd(e,(p-1)*(q-1))=1$
- Alice's public key is the pair (N, e)
- Alice's decryption/private key is d such that: $e*d=1\%((p-1)*(q-1))$
- Alice's private key is the tripe (d, p, q)
### Encryption
- With the PK, Bob can compute C with $c=m^e \%N$
### Decryption
- Decrypt c with $p=c^d\%N$
- 