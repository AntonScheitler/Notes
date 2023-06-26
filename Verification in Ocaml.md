## Big Step Semantics
- In Ocaml every expression $e$, when evaluated is mapped to a value $v$
- Since the intermediate steps in the evaluation of $e$ do not matter, one speaks of big step operational semantics
## Expression Evaluation
- In order to evaluate any expression $e$, rules are defined for how $e$ can be evaluated in certain contexts
#### Notation
- A horizontal line separates the assumptions on a given expression, written above, and the conclusions drawn from those assumptions below
- Using this, rules can be defined for lists, tuples and functions
- Those rules behave similar to how the ocaml runtime would
#### Rules
![[Pasted image 20230626194658.png]]
![[Pasted image 20230626194715.png]]
![[Pasted image 20230626200049.png]]
## Verification
- The conclusions drawn from one expression evaluation can be used as assumptions for following expressions
- Similarly, the conclusions can be used to construct assumptions and thus generate a proof
#### Example
![[Pasted image 20230626202528.png]]
![[Pasted image 20230626202601.png]]
#### Termination
- If an expression can be evaluated to a value, it is proven to terminate
- Termination for all inputs can be proven using induction
###### Example
![[Pasted image 20230626203131.png]]
![[Pasted image 20230626203159.png]]
#### Equality
- Expressions are considered equal, if they both don't terminate, or if they evaluate to the same values for all inputs
- If two expressions have been determined to be equal, they can be used interchangably in other expressions
###### Example
![[Pasted image 20230626203734.png]]