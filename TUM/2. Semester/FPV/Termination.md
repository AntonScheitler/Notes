## General
- It is not guranteed, that an [[Assertions and Verification|assertion]] is always reached, since a program might not terminate
- The termination of a given program must therefore be proven
#### Approach
- For any loop, an indicator value $r$ needs to be identified
- If $r$ fulfills all necessary criteria, a given loop will terminate:
	- $r > 0$ needs to hold, whenever the loop is entered
	- $r$ is decreased on every iteration
- A program might need to be adjusted, in order to create the indicator value $r$
###### Example
![[Pasted image 20230508133734.png]]