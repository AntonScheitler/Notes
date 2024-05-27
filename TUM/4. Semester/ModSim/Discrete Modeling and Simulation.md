## Decision Models
- A decision model, models the behavior of a player trying to maximize an outcome in a set of circumstances
#### Generic Decision Model
- Decisions can be made with certainty, risk or uncertainty, depending on if the rules and actions of a model are known
- A player generally has a set of possible actions $A_1, ..., A_m$ for different states $s_1, ..., s_n$
- Each action $A_i$ for a given state $s_j$ results in a payoff $N_{i, j}$
###### Strategies under Risk
- Since the state of a player may not be known, different approaches are possible
- In a cautios approach, the action is chosen, which results in the best outcome, given the worst possible state
- In a full risk approach, the action is chosen, which results in the best outcome, given the best possible state
- In an alternative cautios approach, the action is chosen, which results in the best outcome, given the state, where the difference in payoffs is greatest
#### Two-Player Zero-Sum Game
- A win player chooses from the actions $A_1, ..., A_m$ and the loss player from $B_1, ..., B_n$
- The result $a_{ij}$ of two actions is considered the payoff from the loss player to the win player
- Therefore the loss players wants to minimize $a_{ij}$, whereas the win player wants to maximize it
###### Decision Making
- The win player assumes, that the loss player chooses the action which minimizes $a_{ij}$ and therefore chooses the action, which maximizes $a_{ij}$ in this case
- The loss player assumes, that the win player chooses the action which maximizes $a_{ij}$ and therefore chooses the action, which minimizes $a_{ij}$ in this case
###### Equilibrium
- The players may reach an equilibrium, where the loss is minimized and the win is maximized
- If an equilibrium is reached, a change in strategy would benefit neither of the players
- Their strategies therefore remain the same
#### Group Decision Making
- A ranking $r$ is assigned to a set of candidates $A$, which measures their importance
- This ranking defines a preference relation $\varrho$ between the candidates:
$$x \varrho y \; \Leftrightarrow \; r(x) < r(y)$$
###### Collective Choice Function
- $P_A$ is a set of preference relations and represents an individuals ranking of all candidates
- A collective choice function takes every individuals $P_A$ into account, in order to create a total $P_A$:
$$K: P_A \times P_A \times ... \times P_A \rightarrow P_A$$
- The resulting preference relation may differ based on the method used to determine it
###### Rank Addition
- The sums of the rankings of each candidate are calculated and compared
- The candidate with the lowest sum wins the majority vote
![[Pasted image 20240511114119.png]]
## Scheduling
- A set of tasks $A_1, ..., A_n$ is run on a set of machines $M_1, ..., M_m$, where each task takes a certain amount of time
- The task execution must be ordered such that the resulting schedule is optimal
- Precedences define, which task needs to be executed before which, creating an ordering of tasks
#### Graph View
- Using tasks as vertices and precedences as edges, a graph view of a schedule can be constructed
- A virtual initial vertex $A_S$ and a virtual final vertex $A_E$ serve as the start and end points of the graph
- The tasks can now be iterated through in topological order
- If tasks are assigned to different machines, they can be iterated through concurrently
###### Schedule Construction
- One option to construct a schedule, is to start every task, as soon as all preceding tasks have been completed
- Alternatively, the completion time of $A_E$ can be used to determine the latest possible time, a task needs to finish at, in order to still meet the completion time of $A_E$ 
- Those approaches are the forward and backward step and they both result in an optimal schedule
###### Example
![[Pasted image 20240516155357.png]]
#### Job Shop
- In a job shop model, tasks are divided into subtasks, which need to run on a specific machine and are all dependent on one another
###### Disjunctive Edges
- If the subtasks $A_{x, y}$ and $B_{i, j}$ of two different tasks happen to be executed on the same machine, a clear ordering cannot be established immediately
- Instead, disjunctive edges, which face from $A_{x, y}$ to $B_{i, j}$ and the other way around, are created
- In a disjunctive edge assignment, each of the edges is tested out, removing the corresponding one
- Using this assignment, an optimal schedule can be determined