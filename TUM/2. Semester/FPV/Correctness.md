## Correctness of a Program
#### Program State
- The state of any given program $\sigma$ can be described by it's variables and their values
- A program state $\sigma$ satisfies a statement $A$, if the statement is true for the current values of all variables
- The correctness of a statement can thus be determined by substituting in all current values
###### Example
![[Pasted image 20230424132008.png]]
#### Execution Trace
- The execution trace $\pi$ of a program is a series of program states $\sigma_0 ... \sigma_m$ with their designated program points $u_0 ... u_m$  
- An execution trace $\pi$ can therefore be described by $$(u_0, \sigma_0)s_1(u_1, \sigma_1)...s_m(u_m, \sigma_m)$$where $s_i$ represents statements, such as basic operations and assignments in the program
#### Theorem
- Using execution traces, the correctness of a program can be verified as follows:
	- Given a program with the execution trace $\pi$ that ranges from the program point $u$ to $v$
	 - The program point $u$ is annotated with the Assertion $A$ and $v$ with $B$
	  - If the initial state of $\pi$ satisfies $A$, then it's final state will satisfy $B$ 