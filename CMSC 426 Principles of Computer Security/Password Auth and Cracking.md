# Authentication
- How do users authenticate themselves to systems
- How do attackers take advantage of these authentication methods
- Hardening: how do we configure systems so that they are secure against attackers?
- Components:
	- Identification
	- Verification
- Means of verifying ID
	- Something a user knows: password, pin, security questions
	- Something a user possesses: keycard, smart card
	- Something a user is: biometrics
	- Something a user does: signature
- Multifactor Auth (MFA)
	- Using more than one category of auth in order to verify a user's identity
	- For example, when you log into your bank account from a new computer:
		- Bank sends a one-time pin number to your phone
		- Have to know the password and possess the phone to authenticate
## Password Authentication
- Why used passwords:
	- They're kind of terrible
	- Prone to user error
	- No one seems to replace them however
- Password managers
	- All of the security of long passwords (with none of the inconvenience)
		- No password reuse across multiple sites
		- Resistant to keyloggers
	- Single point of failure
		- Online storage
		- Local storage: susceptible 
### Password Hashing
- Plaintext passwords should never be stored on disk
- When a user makes an account on a system
	- Their password is hashed
	- The resulting hash digest is stored on disk
- When a user attempts to log in, the password they enter is hashed and compared to the one on disk
### Common Password Auth Features
- Requiring a user to wait between auth attempts
- Locking a user out if they fail to auth multiple times
- These prevent cybercriminals from simply brute-forcing login attempts on a target system
### Distributed Online Password Guessing
- Computers that allow users to log in over a network (such as SSH and RDP) are constantly being scanned by automated password guessers
- Check for computers with default/weak credentials
- Handy for malicious purposes that aren't targeted
	- Botnets, crypto mining
## Salted Passwords
- Password salting is a defense against dictionary attacks and rainbow tables
- When a user creates an account on a system, a random salt is generated for them
- The salt is prepended to their password before it is hashed
- When a user attempts to log in, the salt and password they enter are hashed together and compared to the on on disk
- Password salts stored in plaintext
	- They don't need to be hidden from an attacker to be effective
- For a b-bit salt, the number of possible passwords is increased by a factor of $2^b$ bits
- Because each user has their own salt, attacks involving precomputed hashes cannot be reused
# Offline Password Cracking
- If hackers can gain access to the password hashes on a system, they can perform offline password cracking
- No longer limited by restrictions on target computer, such as limited number of guesses or wait time
## Brute-Force Attack
- Generate the hash of every possible password and check for matches
- Pros
	- Thorough
	- Can crack short passwords easily
- Cons
	- Exponentially more time consuming as passwords get longer
## Dictionary Attacks
- Most users don't use random strings as passwords
	- Passwords tend to contain real words and predictable patterns
- Create a list of potential passwords, hash all of them, and store password-hash pairs in a dictionary
- RockYou
	- Company that made widgets for MySpace
	- Suffered data breach in 2009
	- Passwords were stored in plaintext
	- Now commonly used as a password cracking wordlist
- ![[Pasted image 20230619151820.png]]
- Viability
	- For N passwords:
		- Generating the dictionary is O(N) time
		- The dictionary requires O(N) storage space
		- Looking up a password in the dictionary is O(1)
	- Once generated, can be reused across multiple attacks
	- Not as thorough as brute-forcing - if a target hash isn't in your dictionary, you're out of luck
## Rainbow Tables
- Similar to a dictionary attack
	- Table of pre-computed passwords and corresponding hashes
- Time-memory tradeoff
	- Takes up less space on disk than a dictionary attack
	- Takes more time to perform lookups
- Generate chains of passwords and hashes
	- Only need to store the beginning and end of each chain in the rainbow table
- ![[Pasted image 20230619152148.png]]
- Two different implementations
	1. End the chain when it reaches a certain length
	2. End the chain when a password hash meets a certain condition
- To crack a password hash, generate its chain and check if hashes are in the rainbow table
	- If so, generate the chain from the beginning password in the chain
	- Plaintext password will be located just before the target hash in the chain