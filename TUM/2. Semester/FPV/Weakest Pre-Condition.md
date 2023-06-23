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
- In order to determine the weakest pre-conditions of the statements in a loop and the loop itself, a **loop invariant** needs to be constructed manually
- The loop invariant $B$ is a condition at the end of the loop which holds for every iteration
- The loop invariant is valid, if it implies the weakest pre-condition of the loop
###### Pitfalls in Construction
- If the loop invariant is too weak, it will not imply the weakest pre-condition of the loop
- If the loop invariant is too strong, it might still imply the weakest pre-condition of the loop, but verification will fail at some other program point
###### Best Practices in Construction
- A good invariant should contain all variables involved in the loop
- Since most loops contain a counter, defining variables in relation to that counter makes for a good invariant
- The break condition should also be taken into consideration
- It's recommended to keep track of the different variable's values across multiple iterations and look for patterns
- The invariant should also contain the end result of the program in some, slightly different, form
- In the above example, $z = i^2 \land x = 2i -1$ would be a suitable invariant