- "The prevention of unauthorized use of a resource, including the prevention of use of a resource in an unauthorized manner"
- Central element of computer security
- ==NISTIR 7298== defines access control as: “the process of granting or denying specific requests to: (1) obtain and use information and related information processing services; and (2) enter specific physical facilities”
- ==RFC 4949== defines access control as: “a process by which use of system resources is regulated according to a security policy and is permitted only by authorized entities (users, programs, processes, or other systems) according to that policy”
- ![[Pasted image 20230619154427.png]]
# Policies
- These four policies are not mutually exclusive. An access control mechanism can employ two or even three of these policies to cover different classes of system resources.
- ![[Pasted image 20230619155011.png]]
## Discretionary Access Control (DAC)
- Controls access based on the identity of the requestor and on access rules (authorizations) stating what requestors are (or are not) allowed to do
- Started in 1960's
- Scheme in which an entity may be granted access rights that permit the entity, by its own violation, to enable another entity to access some resource
- Often provided using an access matrix
	- Lists subjects in one dimension (rows)
	- Lists objects in the other dimension (cols)
	- Each entry specifies access rights of the specified subject to that object
- Access matrix is often sparse
- Can decompose by either row or column
- ![[Pasted image 20230619155219.png]]
- ![[Pasted image 20230619155247.png]]
- ![[Pasted image 20230619155308.png]]
- ![[Pasted image 20230619155331.png]]
### Protection Domains
- Set of objects together with access rights to those objects
- More flexibility when associating capabilities with protection domains
- In terms of the access matrix, a row defines a protection domain
- User can spawn processes with a subset of the access rights of the user
- Associate between a process and a domain can be static or dynamic
- In user mode certain areas of memory are protected from use and certain instructions may not be executed
- In kernel mode privileged instructions may be executed and protected areas of memory may be accessed. 
## Role-based Access Control (RBAC)
- Controls access based on the roles that users have within the system and on rules stating what accesses are allowed to users in given roles
- ![[Pasted image 20230619155621.png]]
- ![[Pasted image 20230619155656.png]]
- ![[Pasted image 20230619155716.png]]
- ![[Pasted image 20230619155731.png]]
- ![[Pasted image 20230619155758.png]]
### Constraints
- Provide a means of adapting RBAC to the specifics of admin and security policies of an org
- A defined ralationship among roles or a condition related to roles
- Types: ![[Pasted image 20230619155823.png]]
## Mandatory Access Control (MAC)
- Controls access based on comparing security labels with secuirty clearances
## Attribute-based Access Control (ABAC)
- Controls access based on attributes of the user, the resouce to be accessed, and current environmental conditions
- ![[Pasted image 20230619155946.png]]
- Attributes: ![[Pasted image 20230619160008.png]]
- ![[Pasted image 20230619160023.png]]
- ![[Pasted image 20230619160052.png]]
- ![[Pasted image 20230619160125.png]]
- ![[Pasted image 20230619160138.png]]