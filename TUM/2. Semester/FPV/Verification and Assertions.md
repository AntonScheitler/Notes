## Assertions
- In order to verify the correctness of a given program, assertions can be used
- Assertions throw an exception if the given expression evaluates to false
- In order to verify a program, every program points needs to be annotated with an assertion
#### Example
![[Pasted image 20230417211426.png]]
## Pre- and Post-Conditions
#### Assignment Operation
- The assertion before an assignment operation is called a pre-condition
- The assertion after an assignment operation is called a post-condition
###### Weakest Pre-condition
- In order for a post-condition **B** to be met, a minimal assumption **WP(B)** needs to be fulfilled
- The assumption **WP(B)** is the weakest pre-condition
- Any pre-condition **A** is valid, if it implies the weakest pre-condition **WP(B)**
###### Example
![[Pasted image 20230417212856.png]]
- The strong pre-conditions are all valid, since they imply the weakest pre-condition
- The weakest pre-condition is constructed like so:
	- Given an assignment of **e** (x-y) to **x** (x) and a post-condition, that contains **x** (x > 0), every occurance of **x** needs to be replaced with **e**
	 - Thus the weakest pre-condition in this case is x-y > 0