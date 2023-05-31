## General
- In order to reduce the complexity of a software system, it is broken down into simpler modules
- Those modules solve the challenges posed to the system
#### Architecture
###### Interfaces
- Each module provides an interface, which enables interaction without knowledge of the underlying system
- Ideally, a module should offer deep functionality and abstract away its complexity using a simple interface
###### Cohesion
- Cohesion describes how closely the components of a module work with each other
- This should be maximized
###### Coupling
- Coupling describes how closely multiple components work with each other
- This should be minimized
#### Facade design pattern
- A module should not be exposed by simply making all operations publically available
- A facade should be implemented, which exposes the components of a module in a controlled manner
- This simplifies inter-module interaction
###### Example
![[Pasted image 20230525090157.png]]