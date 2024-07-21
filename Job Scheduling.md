## Scheduling
- A set of tasks $A_1, ..., A_n$ is run on a set of machines $M_1, ..., M_m$, where each task takes a certain amount of time
- The task execution must be ordered such that the resulting schedule is optimal
- Precedences define, which task needs to be executed before which, creating an ordering of tasks
#### Graph View
- Using tasks as vertices and precedences as edges, a graph view of a schedule can be constructed
- A virtual initial vertex $A_S$ and a virtual final vertex $A_E$ serve as the start and end points of the graph
- If tasks are assigned to different machines, they can be iterated through concurrently
###### Schedule Construction
- One option to construct a schedule, is to start every task, as soon as all preceding tasks have been completed
- Alternatively, the completion time of $A_E$ can be used to determine the latest possible time, a task needs to finish at, in order to still meet the completion time of $A_E$ 
- Those approaches are the forward and backward step and they both result in an optimal schedule
###### Critical Paths
- A path in a schedule is critical, if there can be no downtime between tasks on it
###### Example
![[Pasted image 20240516155357.png]]
#### Job Shop
- In a job shop model, tasks are divided into subtasks, which need to run on a specific machine and are all dependent on one another
###### Disjunctive Edges
- If the subtasks $A_{x, y}$ and $B_{i, j}$ of two different tasks happen to be executed on the same machine, a clear ordering cannot be established immediately
- Instead, disjunctive edges, which face from $A_{x, y}$ to $B_{i, j}$ and the other way around, are created
- In a disjunctive edge assignment, each of the edges is tested out, removing the corresponding one
- Using this assignment, an optimal schedule can be determined