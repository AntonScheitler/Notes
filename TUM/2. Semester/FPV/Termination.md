## General
- It is not guranteed, that an [[Assertions and Verification|assertion]] is always reached, since a program might not terminate
- The termination of a given program must therefore be proven
#### Approach
- For any loop, an indicator value $r$ needs to be identified
- If $r$ fulfills all necessary criteria, a given loop will terminate:
	- $r > 0$ needs to hold, whenever the loop is entered
	- $r$ is decreased on every iteration
###### Example
![[Pasted image 20230508133734.png]]
- An $r$ is determined using a combination of local variables $(x + y)$ 
- A pre-condition is formed using this r $(r > x + y)$
- Using this pre-condtion, the other weakest pre-conditions inside the loop are constructed
- The weakest pre-condition at the start of the loop needs to be implied by $r$ $(r = x + y)$ and the loop-condition $(x \neq y)$
- The implying condition can be strengthened in order for the implication to succeed