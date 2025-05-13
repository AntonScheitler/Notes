## Stochastic Processes
- A discrete stochastic process is a series of random variables $(X_n)_{n = 0}^{\infty}$, where $X_n$ denotes the state of the process at time $n$
- Each random variable assumes values in the same finite or countably infinite sate space $E$
## Markov Chains
- A stochastic process is a Markov Chain, if for every $n$ and $x_0, x_1, ..., x_n \in E$ with $P(X_0 = x_0, X_1 = x_1, ... X_n = x_n) > 0$ the following holds:
$$P(X_n = x_n \mid X_0 = x_0, ..., X_{n - 1} = x_{n - 1}) = P(X_n = x_n \mid X_{n - 1} = x_{n - 1})$$
- In other words, the probability of the process reaching a certain state depends only on it's previous state, if it's a Markov Chain
- A Markov Chain in homogenous, if for any two states $i, j \in E$ and any two points in time $n, m \in \mathbb{N}$ with $P(X_{n - 1} = i) > 0$ and $P(X_{m - 1} = i) > 0$ the following holds:
$$P(X_n = j\mid X_{n - 1} = i) = P(X_m = j \mid X_{m - 1} = i)$$
- This means the probability of the stochastic process to transition from state $i$ to $j$ does not change over time, if the process is a homogenous Markov Chain
#### Example
- One example of a Markov Chain is a simple random walk, in which the state space is defined as $E = \mathbb{Z}$ and the chain is based on a series of independent random variables $(Z_n)_{n = 1}^{\infty}$, where $P(Z = 1) = P(Z = -1) = \frac12$
- The simple random walk is then defined as:
$$X_n = \sum_k^n Z_k$$
- This stochastic process is considered a Markov Chain, because the following holds:
$$P(X_n = x_n \mid P_0 = x_0, P_1 = x_1, ..., P_{n - 1} = x_{n - 1}) = $$
$$= P(Z_n = x_n - x_{n - 1} \mid P_0 = x_0, P_1 = x_1, ..., P_{n - 1} = x_{n - 1}) =$$
$$= P(Z_n = x_n - x_{n - 1} \mid Z_1 = x_1,  Z_2 = x_2 - x_1, ..., Z_{n - 1} = x_{n - 1} - x_{n - 2})$$
- Because all $Z_k$ are independent, this can be rewritten as:
$$P(Z_n = x_n - x_{n - 1}) = \frac12 = P(X_n = x_n \mid X_{n - 1} = x_{n - 1})$$
#### Modelling Transitions
- The probabilities for state transitions in a Markov Chain can be modeled by a transition matrix $M \in E \times E \rightarrow [0, 1]$, in which $P(X_n = j | X_{n - 1} = i) = M_{ij}$
- Alternatively, a transition graph can be used, which is a directed graph with a set of verticies $E$ and edges $i \to j$, where an edge $i \to j$ only exists if $P(X_n = j \mid X_{n - 1} = i) > 0$
#### Existance Theorem
- The initial distribution of a Markov Chain is modelled by $\mu$ where $\mu(i) = P(x_0 = i)$ and the following properties hold:
$$\mu: E \rightarrow \mathbb{R}, \; \forall \mu(i) \geq 0, \; \sum_i \mu(i) = 1$$
- According to the existance theorem, a homogenous markov chain can thus be described using the initial distribution $\mu$ and a transition matrix $\pi$
#### Uniqueness in Distribution
- Given a state space $E$, a distribution $\mu$ over $E$, a stochastic matrix $\Pi$ and a stochastic process $(X_n)_{n \in \mathbb{N}_0}$ the following three statements are equivalent:
	1. $(X_n)_{n \in \mathbb{N}_0}$ is a Markov chain
	2. $$\forall n \in \mathbb{N}_0, \:i_0, ..., i_n \in \mathbb{N}_0: P(X_0 = i_0, ..., X_n = i_n) = \mu(i_0) \cdot \prod_{k = 2}^n \Pi(i_{k-1}, i_{k})$$
	3. $$A_0, ..., A_n \subseteq E: P(X_0 \in A_0, ..., X_n \in A_n) = \sum_{i_0 \in A_0} \mu(i_0) \cdot \; ... \; \cdot \sum_{i_n \in A_n} \Pi(i_{n-1}, i_n)$$
- If any two Markov chains $(X_n)_{n \in \mathbb{N}_0}$ and $(Y_n)_{n \in \mathbb{N}_0}$ have the same initial distribution $\mu$ and transition matrix $\Pi$, the distributions of $(X_n)$ and $(Y_n)$ are identical
#### Markov Property
- Let $(X_n)_{n \in \mathbb{N}_0}$ be a Markov chain with the initial distribution $\mu$ and transition matrix $\Pi$ and let $m \in \mathbb{N}_0$ and $k \in E$, with $P(X_m = k) > 0$
- We define $\tilde{X}_n = X_{n + m}$$ and $\tilde{P}(A) = P(A \mid X_m = k)$
- The Markov property states that $(\tilde{X}_n)_{n \in \mathbb{N}_0}$ is now also a Markov chain with the transition matrix $\Pi$ and initial distribution $\delta_k = \begin{cases} 1, \; i_m = k \\ 0, \; i_m \neq k \end{cases}$