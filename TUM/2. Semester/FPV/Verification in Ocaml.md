## Big Step Semantics
- In Ocaml every expression $e$, when evaluated is mapped to a value $v$
- Since the intermediate steps in the evaluation of $e$ do not matter, one speaks of big step operational semantics
## Expression Evaluation
- In order to evaluate any expression $e$, rules are defined for how $e$ can be evaluated in certain contexts
#### Notation
- A horizontal line separates the prerequisites on a given expression, written above, and the conclusions drawn from those prerequisites below
- Using this, rules for the evaluation of every type of expression can be defined
#### Rules
![[Pasted image 20230626194658.png]]
![[Pasted image 20230626194715.png]]
![[Pasted image 20230626200049.png]]
## Verification
- The statement to be proven is the bottom most conclusion
- Using the rules for expression evaluation, prerequisites are drawn from it until only axioms remain
#### Example
![[Pasted image 20230722163724.png]]
#### Termination
- If an expression can be evaluated to a value, it is proven to terminate
- Termination for all inputs can be proven using induction
###### Example
![[Pasted image 20230626203131.png]]
![[Pasted image 20230626203159.png]]
#### Equality
- Expressions are considered equal, if they both don't terminate, or if they evaluate to the same values for all inputs
- If two expressions have been determined to be equal, they can be used interchangably in other expressions
###### Induction
- The equality of two expressions can be proven using induction
- If a statements involves a constant, it needs to be generalized
- In order to reverse generalization, a trace back needs to be specified at the end of the proof
###### Example
```ocaml
type tree = Node of tree * tree | Empty

let rec nodes t = match t with Empty -> 0
    | Node (l,r) -> 1 + (nodes l) + (nodes r)

let rec count t =
  let rec aux t a = match t with Empty -> a
      | Node (l,r) -> aux r (aux l (a+1))
  in
  aux t 0

To prove:
    count t = nodes t

Adaptiation:
    aux t 0 = nodes t

Generalization:
( * ) aux t b = nodes t + b

Proof by induction over t

Base case:
    aux Empty b
(aux) = match Empty with Empty -> b | Node (l,r) -> aux r (aux l (b+1))
(match) = b

(arith) = b
(match) = 0 + b
(nodes) = (match Empty with Empty -> 0 | Node (l,r) -> 1 + (nodes l) + (nodes r)) + b
    nodes Empty + b

I.H aux t b = nodes t + b

Induction Step:
    aux Node(l, r)
(aux) = match Node(l, r) with Empty -> b | Node (l,r) -> aux r (aux l (b+1))
(match) = aux r (aux l (b + 1))
(I.H) = nodes r + (aux l (b + 1))
(I.H) = nodes r + nodes l + (b + 1)
(arith) = nodes l + nodes r + b + 1

(arith) nodes l + nodes r + b + 1
(match) = (1 + (nodes l) + (nodes r)) + b
(nodes) = (match Node(l, r) with Empty -> 0 | Node (l,r) -> 1 + (nodes l) + (nodes r)) + b
    nodes Node(l, r) + b

Trace Back:
    count t
(count) = aux t 0
( * ) = nodes t + 0
(arith) = nodes t
```