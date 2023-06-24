# Kerberos
- Trusted key server system from MIT
- Provides centralised private-key third-party authentication in a distributed network
	- Allows users access to services distributed through network
	- Without the need to trust all workstations
	- Rather all trust a central authentication server
- Two versions 
- Basic third-party authentication scheme
- Has an Authentication Server (AS)
	- Users initially negotiate with AS to identify self
	- AS provides a non-corruptible authentication credential (ticket granting ticket TGT)
- Has a Ticket Granting Server (TGS)
	- Users subsequently request access other services from TGS on basis of users TGT
- ![[Pasted image 20230619134406.png]]
## Kerberos Realms
- A kerberos environment consists of:
	- A kerberos server
	- Clients, all registered with server
	- Application servers, sharing keys with server
- This is called a realm
	- Typically a single admin domain
- If there are multiple realms, the Kerberos servers must share keys and trust
- ![[Pasted image 20230619135332.png]]
## Performance Issues
- See larger client-server installations
- Query Kerberos performance impact
	- Very little if system is poerperly configured
	- Since tickets are reusable
- Kerberos security best assured if server is placed on a separate, isolated machine
- Admin motivation for multiple realms
	- Not a performance issue
# Public Key Infrastructure (PKI)
- Based on users and computers having the right certificates and private and public keys
- PKI is based on five essential components:
	1. Cert management system
	2. Digital cert
	3. Cert Revocation List
	4. Public and private keys, certs
	5. Cert Authorities (CAs)
- ==Certificate Server== is a standards-based PKI implementation that can be used on a worldwide scale, or it can be used only within a corporation
## Certificates
- The second essential component of PKI is the digital cert
- The purpose of a digital certificate is to confirm the identity of the certificate holder
- When you apply for a cert from a CA, the CA first confirms the identity of the person or company requesting the cert.
- The current standard for these certs is X.509v3
- The X.509v3 format of the cert is described in the following RFC: [Format Link](https://datatracker.ietf.org/doc/html/rfc6187)
## Certificate Authorities (CA)
- Cert consists of
	- A public key plus a User ID of the key owner
	- Signed by a third party trusted by community
	- Often govt/bank CA
- Users obtain certs from CA
	- Create keys and unsigned cert -> gives to CA -> CA signs cert and attaches signature -> returns to user
- Other users can verify cert
	- Checking signature on cert using CA's public key
- The certs required for PKI are issued by CAs
- In most cases, CAs are configured in hierarchical structure
- A root CA is located at the top of the hierarchy, and subordinate CAs that actually issue the certs are located under the root
- The really important question is "who issued the cert to the user"
- A user can get a cert from any one of hundreds of commercial CAs or may even have a cert from an internal CA in another company
- The cert is only as trustworthy as the issuing CA
- This process of checking out whether a CA is trusted is built on trust paths
- As mentioned earlier, CAs are usually organized in a hierarchical config, with a root CA and a number of subordinate CAs underneath the root
- There can also be several levels of subordinate CAs with each subordinate CA receiving its cert from the CA above it in the hierarchy
- This hierarchy forms a trust path, which means that all of the certs handed out by any CAs in the hierarchy share a common trust path
- ![[Pasted image 20230619141557.png]]
### X.509 Authentication Service
- Universally accepted standard for formatting public-key certs
	- Widely used in network security applications, including IPSec, SSL, SET, and S/MIME
- Part of CCITT X.500 directory service standards
- Uses public-key crypto and digital signatures
	- Algorithms not standardised, but RSA is recommended
- ![[Pasted image 20230619140958.png]]
- ![[Pasted image 20230619141030.png]]
- ![[Pasted image 20230619141054.png]]
## PKIX Management
- Functions:
	- Registration: whereby a user first makes itself known to a CA, prior to issue of certificate(s) for that user. It usually involves some offline or online procedure for mutual authentication
	- Initialization: to install key materials that have the appropriate relationship with keys stored elsewhere in the infrastructure.
	- Certification: process in which a CA issues a cert for a user's public key, and returns that cert to the user's client system and/or posts it in a repo
	- Key pair recovery: a mechanism to recover the necessary decryption keys when normal access to the keying material is no longer possible
	- Key pair update: key pairs need to be updated regularly and new certs issued
	- Revocation request: when authorized advises a CA of a situation requiring cert revocation, e.g. private key compromise, affiliation change, name change. 
	- Cross certification: when two CAs exchange information used in establishing a cross-certificate.  A cross-certificate is a certificate issued by one CA to another CA that contains a CA signature key used for issuing certificates.
- Protocols: CMP, CMC
- The PKIX working group has defines two alternative management protocols between PKIX entities. RFC 2510 defines the certificate management protocols (CMP), which is a flexible protocol able to accommodate a variety of technical, operational, and business models. RFC 2797 defines certificate management messages over CMS (RFC 2630) called CMC. This is built on earlier work to leverage existing code.
## Federated Identity Management
- Use of common identity management scheme
	- Across multiple enterprises and numerous applications
	- Supporting many thousands, even millions of users
- Principal elements are:
	- Authentication: confirmating user corresponds to the user name provided.
	- Authorization: granting access to services/resources given user authentication.
	- Accounting: process for logging access and authorization
	- Provisioning: enrollment of users in the system.
	- Workflow automation: movement of data in a business process.
	- Delegated administration: use of role-based access control to grant permissions.
	- Password synchronization: Creating a process for single sign-on (SSO) or reduced sign-on (RSO).
	- Self-service password reset: enable user to modify their password
	- Federation: process where authentication and permission will be passed on from one system to another, usually across multiple enterprises, reducing the number of authentications needed by the user.
- Kerberos contains many of these elements
- ![[Pasted image 20230619142432.png]]
- ![[Pasted image 20230619142450.png]]
### Standards used
- Exensible Markup Language (XML)
- SOAP: for invoking code using XML over HTTP
- WS-Security: set of SOAP extensions for implementing message integrity and confidentiality in Web services
- Security Assertion Markup Language (SAML): XML-based language for the exchange of security information between online business partners