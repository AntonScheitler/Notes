## Faults and Errors
- A fault is the cause of an error in a system
- If an error occurs, the system is likely to misbehave and thereby fail
- In order to ensure the system does not misbehave, it is validated via observation under different circumstances
#### Dealing with Faults
- Best practices to avoid faults are to reduce complexity and implement [[Fault Tolerance|fault tolerant]] systems
- Faults are detected using testing which provokes failures and corrected through the process of monitoring and debugging
## Testing Types
- The verification process needs to be adjusted to different circumstances, as such different types of testing exist
#### Unit Testing
- A single class or method of the system is tested
###### Black Box Testing
- The testing is focused on the input/ouput behavior of components
- If a component functions the way it should, it's ouput can be predicted given an input
- The number of test cases is reduced using representative inputs via equivalence partitioning
###### White Box Testing
- The testing is focused on the branching of the program
- Test inputs are selected, such that the program executes every statement and all branches are covered
#### Integration Testing
- The interaction between and interfaces of all components of the system is tested
###### Bottom-Up Integration
- Bottom-level components are implemented and tested first
![[Pasted image 20230622093106.png]]
###### Top-Down Integration
- Top-level components are implemented and tested first
![[Pasted image 20230622093234.png]]
###### Stubs, Drivers and Mocks
- If a bottom-level component is not yet implemented, it's interface needs to be replaced by a stub, which returns predetermined values
- If a top-level component is not yet implemented, it's replaced by a driver, which invokes all of it's operations to test other components
- In more complex situations, mocks can be used to more precisely imitate interactions with a component
###### Vertical Integration
- The testing process is focused on specific scenarios that require some of the systems components
- Tests can be executed as soon as a scenario is covered
![[Pasted image 20230622094444.png]]
#### System Testing
- The system as a whole is tested
###### Fuzzing
- The system is tested using random and abnormal inputs with the goal of provoking a failure
- Different fuzzing approaches take the program into account to different degrees
###### Symbolic Execution
- Inputs are replaced with mutable symbols
- The symbols evaluate to different values if a branch is encountered, such that all branches are covered
- If a bug is encountered, the path that lead to it can be reproduced