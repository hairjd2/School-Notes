# Definitions
- Cryptography
- Cryptanalysis
- Cryptology
- Plaintext
- Ciphertext - output of an encryption algo
- Cipher - cryptographic algo
- Algorithm
- Key
- Encryption
- Decryption
# Encryption
- Encryption involves the changing of data into an indecipherable form before transmission.
## Confusion and Diffusion
- Important concepts in cryptography and evaluation effectiveness
- Confusion
	- Each bit of the ciphertext should depend on several parts of the key
	- Obscures the connection between key and outcome
- Diffusion
	- If a single bit of the plaintext changes, (statistically) about half of the bits in the ciphertext should change
## Symmetric Encryption
- ![[Pasted image 20230619000241.png]]
### Historical Ciphers
- Caesar cipher
- Atbash cipher
	- Reversal of the alphabet
- Keyword cipher
	- Keyword "begins" the alphabet, rest follows in order
	- "Cryptography": CRYPTOGAHBDEFIJKLMNQSUVWXZ
- Vigenere cipher
	- Keyword is repeated, and is used to shift plaintext into ciphertext
	- ![[Pasted image 20230619000930.png]]
	- ![[Pasted image 20230619000948.png]]
	- ![[Pasted image 20230619001037.png]]
### Block Ciphers
- Process the plaintext in fixed-size "blocks"
- Ciphertext produced is of blocks of equal size
- Block ciphers are symmetric algorithms
	- Key ramains the same for encryption and decryption
	- However, two separate algorithms for encryption/decryption
- Most commonly-used algorithms are DES, 3DES, and AES
#### Modes of Operation
- Block ciphers themselves are only good for encrypting a block
	- Repeatedly applying a block cipher to larger amounts of data requires a mode of operation
	- Some modes require an Initialization Vector to get started
- Different modes
	- Efficiency
	- Parallel encrypt and/or decrypt
	- Encrypting a stream
- ![[Pasted image 20230619010330.png]]
- ![[Pasted image 20230619010632.png]]
- ![[Pasted image 20230619010649.png]]
- ![[Pasted image 20230619011122.png]]
- ![[Pasted image 20230619011144.png]]
- ![[Pasted image 20230619011212.png]]
- ![[Pasted image 20230619011227.png]]
- ![[Pasted image 20230619011240.png]]
#### Components
- Block size: size in bits of a block (commonly 128 bits)
- Key size: size in bits of the key (commonly 128 bits)
- Round function: basic encryption function; iterated to form the encryption algorithm
- Number of rounds: the number of iterations of the round function
- Subkey algorithm: algorithm that expands the key into multiple round keys
- ![[Pasted image 20230619012137.png]]
#### Feistel Networks
- Iterative structure used in the DES and 3DES algorithms
	- Split 64 bits of input into right and left blocks
	- Apply Feistel function to the right half of the data
	- XOR it using the left half of the data
	- Swap the two blocks for the next round
	- Each of the 16 rounds is identical
		- (Which is why we swap the data’s sides)
		- Only difference is the subkey used in the Feistel function
#### Feistel Function
- Consists of four stages, done on 32 bits of data
- Expansion: 32 bits is expanded to 48 bits (eight 6 bit pieces, which each contain a copy of the adjacent bit on each side)
- Key mixing: XOR'd with 48-bit subkey
- Substitution: divided into eight 6 bit pieces again, which are processed by the substitution boxes (S-box)
	- Turns 6 bits in 4 bits according to a non-linear transformation (provided by a lookup table)
	- Core component of the security of DES; without these, it would be trivial to break
- Permutation: outputs are rearranged according to a fixed permutation, so that the same bits don’t go through the same substitution box again together
### DES (Data Encryption Standard)
- Blocks are 64 bits
- Key is 56 bits
	- Actually 64 bits, but every 8th bit is a parity bit
- Algorithm itself is very secure
	- Very well-studied, and no reported fatal weaknesses
- Key size is woefully small
	- Only 72,000,000,000,000,000 possible keys
	- Can be brute-forced by a powerful machine in about an hour
### Triple DES (or 3DES)
- Uses 3 keys, for a total key size of 168 bits
- Encrypts with one key at a time
- If only two keys, just uses key 1 as key 3
- Three times as slow as DES... not good for large encryption jobs
### Advanced Encryption Standard (AES)
- Is also a block cipher, but does not use feistel networks
- Instead of splitting data in half and using one half to modify the other, AES processes the entire data block in parallel
- Block length is 128 bits, and key can be 128, 192, or 256
	- We will just assume it is 128 bits, meaning that AES performs 10 rounds
- Decryption is still performed with keys applied in reverse
	- But encryption and decryption algorithms are not identical as in DES
- ![[Pasted image 20230619014605.png]]
- ![[Pasted image 20230619014615.png]]
- ![[Pasted image 20230619014627.png]]
- ![[Pasted image 20230619014640.png]]
- ![[Pasted image 20230619014956.png]]
- ![[Pasted image 20230619015006.png]]
## Asymmetric Encryption
### Shortcomings of Symmetric Encryption
- Symmetric key must remain secret to be secure
- But how do you communicate what the secret key is?
- Need some way to share keys over an unsecured channel
### Diffie-Hellman Key Exchange
- Named after Whitfield Diffie and Martin Hellman
- It is a way for two parties to 
	- Use insecure communication to
	- Agree on a cryptographic key
	- Without anyone else being able to figure out what it is
- Neither party "chooses" the key, but that doesn't matter
	- They just need the same one
#### Algorithm
- Choose two ==non-secret== values *p* and *g*
	- *p* is prime
	- *g* is generator, a primitive root modulo p
- Each party
	- Chooses an integer *Y* in the range 1 to p-1 (inclusive)
	- Calculates $y=g^Y\%p$ and transmit *y* across the clear channel
	- Use the other party's transmitted integer (x) to calculate $K=x^Y\%p$
- Both parties now have the same value *K*, for a symmetric key
- ![[Pasted image 20230619002831.png]]
- ![[Pasted image 20230619003914.png]]
- p, g, a, and b are transmitted, so a hacker would need A or B to calculate K
### RSA Overview
- Pick two secret prime numbers, p and q
	- With those values, calculate *n* = *p* * *q*
- Choose a valid public exponent *e*
	- Software today uses 65537 (0x10001) to make calculations faster
		- A valid e is not a factor of n, and must be less than $d\%(p-1)*(q-1)$
- Calculate a private exponent d
	- Such that e is congruent to $d\%(p-1)*(q-1)$
- Public key components are n and e
- Private key components are n and d (normally save p and q too)
- Encryption
	- The plaintext P is converted into an integer m
	- $C=m^e\%n$ (remember, e and n were our public key components)
- Decryption
	- $m=C^d\%n$ (remember, d and n were our private key components)
- Mathematical proof
	- Outside of the scope of this class
- ![[Pasted image 20230619005434.png]]
- ![[Pasted image 20230619005444.png]]
- ![[Pasted image 20230619005531.png]]