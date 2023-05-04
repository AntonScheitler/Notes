## Cloud Computing
#### General
- Cloud computing is the delivery of software services over the Internet
- Cloud providers offer the resources needed to deploy software to the cloud
- This approach offers higher scalability and reliablility
- Cloud providers can offer different types of [[Cloud Services|services]]
## Distributed Software Systems
- A distributed system is an application, that executes protocols over multiple computers connected via a network
- An example of a distributed system is a client-server application
#### Client-Server Applications
- The client application is  built on data received from a server
- The client thus has to make requests to a server, which provides the appropriate response
- Client and server can communicate via remote procedure calls 
###### Remote Procedure Calls
- The desired procedure, or function on the server is called by the client
- The client also specifies the necessary arguments to the procedure
- Since the client and server might be written in different languages, the data passed between them must be serialized
## Deployment Models
- The process of delivering software from a development environment to a production environment is called deployment
- There are different models for deployment
#### Baremetal
- The entire physical machine needs to be managed
- This offers full control and higher performance
###### Workflow
- During provisioning, the operating system is installed
- During deployment, the application is installed and run
![[Pasted image 20230427095917.png]]
#### Virtual Machines
- Multiple [[Virtualization|VMs]] run on a single machine with separate operating systems and shared physical resources
- VMs offer higher scalablility than baremetal
###### Workflow
- During provisioning, the virtual machine is created using a VM image
- During deployment, the application is installed and run
![[Pasted image 20230427101506.png]]
###### Example
![[Pasted image 20230427101221.png]]
#### Containers
- Linux containers provide a contained environment for applications and their dependencies
- Multiple containers run on a single operating system and share the host's resources
- The containers are executed using a container engine
###### Workflow
- The container image is provided to the engine
- During deployment, the engine starts the containers
![[Pasted image 20230427102601.png]]
###### Example
![[Pasted image 20230427102621.png]]
#### Serverless
- The server infrastructure is managed entirely by the cloud provider
- Provisioning and scaling are thus managed by the provider
###### Workflow
- The application image is uploaded to the serverless platform
- The platform takes care of running and scaling the application
![[Pasted image 20230427103800.png]]
###### Example
![[Pasted image 20230427103927.png]]
