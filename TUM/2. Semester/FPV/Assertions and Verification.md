## Assertions
- In order to verify the correctness of a given program, assertions can be used
- Assertions throw an exception if the given expression evaluates to false
- In order to verify a program, every program points needs to be annotated with an assertion
- The assertion before an operation is called a pre-condition
- The assertion after an operation is called a post-condition
#### Example
![[Pasted image 20230417211426.png]]
## Verification
- Each program points needs to be annotated with an assertion with the start being annotated with true
- For each statement (or conditional ) $s$ the given assertion $A$ needs to imply the [[Weakest Pre-Condition|weakest pre-condition]], derived from the post-condition $B$ (or $B_0$ and $B_1$) of $s$
- If this is fulfilled, the assertions is considered locally consistent