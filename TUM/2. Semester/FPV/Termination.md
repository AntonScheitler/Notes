## General
- It is not guranteed, that an [[Assertions and Verification|assertion]] is always reached, since a program might not terminate
- The termination of a given program must therefore be proven
#### Approach
###### Indicator Variable
- For any loop, an indicator variable $r$ needs to be determined
- $r$ ist often calculated using an expression $e_r$, composed of local variables
###### Control Flow
- The necessary operations for creating and updating $r$ are inserted into the program
- The loop invariant is formed around $r$
###### Proof
- Locally consistent assertions are calculated inside the loop via [[Weakest Pre-Condition|weakest pre-conditions]], starting with the assertion $r > e_r$
- If $r$ fulfills all necessary criteria, a given loop will terminate:
	- The assertion at the start of the loop implies $r \geq 0$
	- The assertion at the end of the loop implies $r > e_r$
###### Example
![[Pasted image 20230627195811.png]]