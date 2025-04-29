## Stochastic Processes
- A discrete stochastic process is a series of random variables $(X_n)_{n = 0}^{\infty}$, where $X_n$ denotes the state of the process at time $n$
- Each random variable is identically distributed and assumes values in the same finite or countably infinite sate space $E$
#### Markov Chains
- A stochastic process is a Markov Chain, if for every $n$ and $x_0, x_1, ..., x_n \in E$ with $P(X_0 = x_0, X_1 = x_1, ... X_n = x_n) > 0$ the following holds:
$$P(X_n = x_n \mid X_0 = x_0, ..., X_{n - 1} = x_{n - 1}) = P(X_n = x_n \mid X_{n - 1} = x_{n - 1})$$
- In other words, the probability of the process reaching a certain state depends only on it's previous state, if it's a Markov Chain
- A Markov Chain in homogenous, if for any two states $i, j \in E$ and any two points in time $n, m \in \mathbb{N}$ with $P(X_{n - 1} = i) > 0$ and $P(X_{m - 1} = i) > 0$ the following holds:
$$P(X_n = j\mid X_{n - 1} = i) = P(X_m = j \mid X_{m - 1} = i)$$
- This means the probability of the stochastic process to transition from state $i$ to $j$ does not change over time, if the process is a homogenous Markov Chain
###### Modelling Transitions
- The probabilities for state transitions in a Markov Chain can be modeled by a transition matrix $M \in E \times E \rightarrow [0, 1]$, in which $P(X_n = j | X_{n - 1} = i) = M_{ij}$
- Alternatively, a transition graph can be used, which is a directed graph with a set of verticies $E$ and edges $i \to j$, where an edge $i \to j$ only exists if $P(X_n = j \mid X_{n - 1} = i) > 0$