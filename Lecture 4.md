- Can hide all of the libraries they use by having only one import from a bunch of dll's, then have LoadLibrary and GetProcAddress
- # Lecture 3 Refresh

## Entropy:

- byte has 2^8 possible values, so a truly random sequence has an entropy of 8
- executable code usually has entropy of around 4-6
- encrypted or obfuscated data typically has an entropy over 7, gets close to 8

## Runtime Linking

- malware authors want analyzing to be hard, so they hard a file's imports until it is run
    
    - called runtime linking
        
        - resolves imports as the file runs
        - can import functions that are not listed in the IAT
        
    

### How it works:

- LoadLibrary - gets a handle to any DLL file on a system
- GetProcAddress - gets address of any function in a DLL
- When used together this allows for a program to import a function from any DLL
- Other ways to do runtime linking but this is most common way

# Using a VM for Malware Analysis
## Safe Malware Inside Sandbox
- ![[Pasted image 20230918182002.png]]
- Not attached is the default if the malware doesn't use the internet
- Never use NAT because it would give malware open access
- Bridged Adapter is never used
- Internal network tries to simulate the open internet
- Host-Only Adapter tries to listen to certain internet protocols to provide a spoofed resource
- 