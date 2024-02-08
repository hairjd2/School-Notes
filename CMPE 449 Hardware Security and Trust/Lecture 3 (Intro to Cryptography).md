# Block Cipher
- Cipher with a fixed size
- Needs to wait for the whole message to be sent
- Block size = "o(message length)"
	- Because R must wait for "almost" the entire C before R can decode some characters near beginning of P
## Primitives
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
- 