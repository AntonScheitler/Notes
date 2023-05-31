## Requirements Engineering
- Requirements engineering is the process of managing requirements to a system given a set of features and constraints
####  Requirements
- Requirements are provided from a user's point of view and thus focus more on functionality as opposed to system design
###### Functional Requirements
- Functional requirements are explicit requirements provided by the customer, which have to be met
###### Non-Functional Requirements
- Non-functional requirements are not explicitly provided by the customer
- They are requirements that the system needs to meet in order fulfill functional requirements
- Those include performance, reliability and maintainability
## Software Architectures in the Cloud
- There are different ways of archetecting software that runs in the cloud
#### Three-Tier Architecture
- A three-tier architecture consists of a presentation, application and data layer
###### Presentation
- A UI is served to the user
- This layer manages the interactions between the user and the application
###### Application
- Handles the business logic of the application
- Processes requests from the user and responds accordingly
###### Data
- Persists data needed by the application layer
- Provides the application with the data it needs to respond to the user
###### Communication
- The different layers need to be able to communicate with each other
- This communication can be managed using Remote Procedure Calls and REST
- REST is a communication standard which allows data to be passed via GET, POST, PUT and DELETE requests
#### Monolithic Architectures
- All components of an application are contained in a single package
###### Single-Process Monolith
- In a single-process monoliths, all the components are tightly coupled
![[Pasted image 20230504094624.png]]
###### Modular Monolith
- In a [[Modularity|modular]] monolith, the components are modularized but still contained in a single package
![[Pasted image 20230504094652.png]]
###### Benefits
- Monoliths are more performant
- Scaling can be achieved by simply deploying multiple instances
![[Pasted image 20230504095824.png]]
###### Drawbacks
- Monoliths are less reliable, since a bug in a single component can cause a crash of the whole application
#### Microservice Architecture
- A microservice architecture is built from independent and loosely coupled components
- Those components are called microservices and each serve a specific purpose
###### Benefits
- Since the failure of a component does not impact the rest of the application, this architecture is more reliable
- Since the components are independent, they can be scaled more efficiently
![[Pasted image 20230504100116.png]]
###### Drawbacks
- The higher complexity makes for a slower development process
- Interservice communication introduces latency and vulnerabilities
###### Example
![[Pasted image 20230504095154.png]]