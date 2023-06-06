## Security Engineering
- In order for a sytem to be secure, it needs to follow certain principles
#### Design Principles
###### Compartilization
- A system is devided into [[Modularity|modular]] components, which communicate with each other using a well-defined protocol
###### Least Privilige
- TODO
###### Isolation
- TODO
#### Access Control
- Access control is the practice of managing access to different parts of a system
- This can be achieved through different methods
###### Access Control Lists
- An access control list stores all users and their permissions associated with the system resources
- This data is stored in a matrix
![[Pasted image 20230601084623.png]]
###### Confused Deputy Problem
- TODO
###### Capabilities
- TODO
## Security in the cloud
- The data of applications deployed in the cloud needs to be secure during computation, transmission and storage
#### Computation
- TODO
#### Network
- A network needs to have certain properties in order to be secure
###### Service authenticity
- In order to ensure that a given server is credible, certificates are used
- If a server provides a valid certificate, it can be communicated with
###### Secure communication
- Encryption and authentication needs to be used when communicating over the internet
- Protocols, such as TLS grant these capabilities
- During a TLS handshake the client and server verify each other and exchange keys for encrypted communication
![[Pasted image 20230601091613.png]]
###### Service availability
- TODO