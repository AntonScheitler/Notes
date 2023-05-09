## General
- In order for a post-condition $B$ to be met, a minimal assumption $WP(B)$ needs to be fulfilled
- The assumption $WP(B)$ is the weakest pre-condition
- Any pre-condition $A$ is valid, if it implies the weakest pre-condition $WP(B)$
- The construction of the weakest pre-condition depends on a given instruction
#### Assignment
![[Pasted image 20230417212856.png]]
- The strong pre-conditions are all valid, since they imply the weakest pre-condition
- The weakest pre-condition is constructed like so:
	- Given an assignment of $e$ (x-y) to $x$ (x) and a post-condition, that contains $x$ (x > 0), every occurance of $x$ needs to be replaced with $e$
	 - Thus the weakest pre-condition in this case is $x-y > 0$
#### Conditional
![[Pasted image 20230424222851.png]]
- The weakest pre-condition is derived from the conditional itself, as well as the following statements:
$$WP[b] (B_0, B_1) = (\neg b \land B_0) \lor (b \land B_1)$$
#### Loop
![[Pasted image 20230508123523.png]]
- In order to determine the weakest pre-condition of the statements in a loop, a **loop invariant** needs to be determined
- The loop invariant $B$ is a condition at the end, or start of the loop, which holds for every iteration
- The loop invariant is valid, if it implies the weakest pre-condition of the loop
###### Construction of the loop invariant
- TODO