## Assertions
- In order to verify the correctness of a given program, assertions can be used
- Assertions throw an exception if the given expression evaluates to false
- In order to verify a program, every program points needs to be annotated with an assertion
- The assertion before an operation is called a pre-condition
- The assertion after an operation is called a post-condition
#### Example
![[Pasted image 20230417211426.png]]
#### Weakest Pre-condition
- In order for a post-condition **B** to be met, a minimal assumption **WP(B)** needs to be fulfilled
- The assumption **WP(B)** is the weakest pre-condition
- Any pre-condition **A** is valid, if it implies the weakest pre-condition **WP(B)**
- The construction of the weakest pre-condition depends on a given instruction
###### Assignment
![[Pasted image 20230417212856.png]]
- The strong pre-conditions are all valid, since they imply the weakest pre-condition
- The weakest pre-condition is constructed like so:
	- Given an assignment of **e** (x-y) to **x** (x) and a post-condition, that contains **x** (x > 0), every occurance of **x** needs to be replaced with **e**
	 - Thus the weakest pre-condition in this case is x-y > 0
###### Conditional
![[Pasted image 20230424222851.png]]
- Again, for the pre-condition A to be valid, it needs to imply the weakest pre-condition
![[Pasted image 20230424223008.png]]
- The weakest pre-condition can be rewritten like so:
![[Pasted image 20230424223104.png]]
## Verification
- Each program points needs to be annotated with an assertion with the start being annotated with true
- For each statement (or conditional ) $s$ the given assertion $A$ needs to imply the weakest pre-condition, derived from the post-condition $B$ (or $B_0$ and $B_1$) of $s$
- If this is fulfilled, the assertions is considered locally consistent