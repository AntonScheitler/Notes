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
#### Weak Markov Property
- Let $(X_n)_{n \in \mathbb{N}_0}$ be a Markov chain with the initial distribution $\mu$ and transition matrix $\Pi$ and let $m \in \mathbb{N}_0$ and $k \in E$, with $P(X_m = k) > 0$
- We define $\tilde{X}_n = X_{n + m}$ and $\tilde{P}(A) = P(A \mid X_m = k)$
- The weak Markov property states that $(\tilde{X}_n)_{n \in \mathbb{N}_0}$ is now also a Markov chain with the transition matrix $\Pi$ and initial distribution $\delta_k = \begin{cases} 1, \; i_m = k \\ 0, \; i_m \neq k \end{cases}$ and therefore independent of all $(X_i)_{i = 0}^m$
#### Reachability and Communication
- A state $j \in E$ is considered reachable from $i \in E$, if the following holds: 
$$\exists n \in \mathbb{N}_0: P(X_n = j \mid X_0 = i) > 0$$
- This relationship between $j$ and $i$ can also be expressed by $i \rightarrow j$
- $i$ and $j$ communicate, if both $i \rightarrow j$ and $j \rightarrow i$ hold, resulting in $i \leftrightarrow j$
###### Proving Reachability
- $i \rightarrow j$ holds if $\exists n: \Pi^n(i, j) > 0$ which is equivalent to saying $\sum_n \Pi^n(i, j) > 0$
###### Communication Classses
- Communication between states is an equivalence relation, meaning that the state space can be divided into communication classes
- If the entire state space $E$ has only one communication class, the Markov chain is considered irreducible, otherwise it is reducible
###### Closed Sets
- A set $I \subseteq E$ is closed if the following holds:
$$\forall i \in I: \sum_{j \in I} \Pi(i, j) = 1$$
#### Periodicity
- For any $i \in E$ we define the following set:
$$T(i) = \{n \geq 1: \Pi^n(i, i) > 0\}$$
- The period of $i$ is then defined as the greatest common divider of $T(i)$, where the $gcd = \infty$, if $T(i) = \emptyset$
###### Periodicity of a Markov Chain
- For two states $i$ and $j$ with $i \leftrightarrow j$, it holds that these two states have the same period
- From this it also follows that every state in an irreducible Markov chain has the same period
- If this is the case, this period is the period of the Markov chain
- A chain with a period of $1$ is considered aperiodic, one with a period $> 1$ is considered periodic
###### Consequences
- Given an irreducible Markov chain with a transition matrix $\Pi$ and a period of $p$, then for any two states $i$ and $j$ there exist an $m$ and $n_0$, so that the following holds:
$$\forall n \geq n_0: \Pi^{n \cdot d + m}(i, j)$$
- Additionally, if a Markov chain is irreducible, aperiodic and has a finite state space, then there exists an $n_0$ so that the following holds:
$$\forall n \geq n_0: \Pi^n(i, j) > 0$$
- If an irreducible Markov chain has a period of $d$, it can be divided into $d$ groups $C_0, ..., C_{d - 1}$, for which the following holds:
$$\forall i \in C_k: \sum_{j \in C_{k + 1}} \Pi(i, j) = 1$$
#### Stopping Times
- Given a probability space $(\Omega, F, P)$, the sequence of [[Kontinuierliche Wahrscheinlichkeitsraeume|sigma algebras]] $(F_n)$ is called a filtration, if $\forall n: F_n \subseteq F_{n + 1} \subseteq F$
- For a stochasitc process $(X_n)$, such a filtration can be generated by $\sigma(X_1, X_2, ..., X_n)$ and is called a natural filtration
- Essentially, the $i$th sigma algebra in the natural filtration of a Markov chain contains all the events that can be described by the all random variables $X_i$ up to that point
- A random variable $\tau$ that is defined on this probability space is called a stopping time if this holds:
$$\forall n : \{\tau \leq n\} \in F_n$$
- Intuitively, for a natural filtration of a stochastic process, this means that for every step of the process, one needs to be able to decide if the event represented by $\tau$ is satisfied just by what has happened up to that time
- In other terms, the event that describes that a stopping time is met, e.g. $\{\tau = n\}$, must be included in the appropriate sigma algebra $F_n$ of the Markov chain $(X_n)$ at time $n$
- If $\tau$ is satisfied then the process can be stopped, meaning that no knowledge of the future is required to determine whether or not to stop the process
###### Strong Markov Property
- Let $(X_n)$ be a Markov chain, $k \in E$, $\tau$ be a stopping time with respect to the natural filtration of $(X_n)$ and let the stopped Markov chain $(X_{n \land \tau})$ be defined as such:
$$X_{n \land \tau} = \begin{cases}
X_n,  \; \text{if} \; n < \tau \\
X_{\tau},  \; \text{if} \; n \geq \tau \\
\end{cases}$$
- Then conditioned on the event $(\tau < \infty, X_{\tau} = k)$, a Markov chain $(Y_n)$ can be defined via $Y_n = X_{n + \tau}$,
- $(Y_n)$ then has the transition matrix $\Pi$ and the initial distribution $\delta_k$ and is independent of the stopping time $\tau$ and the stopped Markov chain $(X_{n \land \tau})$
## Stationary Distributions
- A probability vector $a$ is a stationary distribution for a Markov chain on a state space $E$ with transition matrix $\Pi$, if for every $i \in E$ the following holds:
$$\sum_{j \in E} a(j) \cdot \Pi(j, i) = a(i)$$
- Written differently, it means the following holds for $a$:
$$a\Pi = a$$
- This means that if the initial distribution of a Markov chain is a stationary distribution $a$, then:
$$\forall n \in \mathbb{N}, i \in E: P(X_n = i) = a(i)$$
#### Determining the Distribution
- In order to determine $a$, the following system of equasions needs to be solved:
$$\begin{cases}
a \Pi = a \\
\sum_{i \in E} a(i) = 1 \\
\end{cases}$$
- This means a Markov chain can have one, infinitly many or no stationary distributions
#### Reversability
- A Markov chain is reversible, if there is a distribution $a$, so that:
$$\forall i, j \in E: a(i) \Pi(i, j) = a(j) \Pi(j, i)$$
- In other words, it is reversible if, given some distribution $a$, it is as likely to go from any state $i$ to a state $j$ as it is to go from $j$ to $i$ in a single step
- Additionally, any reversable distribution of a Markov chain is also stationary
## Transience and Recurrence
- Let $(X_n)$ be a Markov chain with a transition matrix $\Pi$ and state space $E$, where $i \in E$
- The state $i$ is called recurrent, if $Pr(T_i < \infty) = 1$ and transient, if $Pr(T_i < \infty) < 1$, where $T_i = \inf\{n > 0: X_n = i\}$, i.e. $T_i$ is the smallest $n$ for which the Markov chain reaches $i$ again
- In other words, a state is recurrent, if it is guaranteed that the state will be reached again and again in finite time and it is transient, if this is not guaranteed
- Overall, a state $i$ is recurrent if and only if the following holds:
$$\sum_{n = 0}^{\infty} \Pi^n(i, i) = \infty$$
- Also, if $i$ is recurrent then all the states that are in the same communication class as $i$ are recurrent 
- If all states in a Markov chain are recurrent, then the chain itself is also considered recurrent, otherwise it is considered transient
- A state $i$ is positive recurrent, if $\mathbb{E}(T_i) < \infty$ and null recurrent, if $\mathbb{E}(T_i) = \infty$
- Additionally, a stationary distribution exists if and only if the given Markov chain is positive recurrent
## Invariant Measures
- Let $(X_n)$ be a Markov chain with the transition matrix $\Pi$ on the state space $E$
- A function $\alpha: E \to \mathbb{R}$ is called an invariant measure, if the following holds:
$$\forall i: \alpha(i) \geq 0$$
$$\exists i: \alpha(i) > 0$$
$$\alpha \cdot \Pi = \alpha$$
- A stationary distribution is therefore an example of an invariant measure, in this case with the additional condition that all it's element need to sum to $1$
- If a Markov chain is recurrent, then it always has an invariant measure, and if it is also irreducible, then the invariant measure $\alpha$ is unique up to multiplication with a constant
- If $\sum_{i \in E} \alpha(i) < \infty$ holds for that same invariant measure then the chain is positive recurrent
- Given an irreducible and recurrent Markov chain, with $0 \in E$ and $T_0 = \inf\{n \geq 1: X_n = 0\}$, an invariant measure can be constructed like so:
$$\alpha(i) = \mathbb{E}^0\left [ \sum_{n = 1}^{T_0} 1_{X_n = i} \right ]$$
- Here $\mathbb{E}^0$ is the expectation starting with $X_0 = 0$
- Furthermore, it holds that that $\alpha(0) = 1$ and $\forall i \neq 0: a(i) > 0$
- This means that any invariant measure of an irreducible Markov chain is positive for all values
#### Recurrence and Stationary Distribution
- If a markov chain is positive recurrent, then it also has a stationary distribution
#### $\alpha$-reversed Transition Matrix
- Given a Markov chain $(X_n)$ on a state space $E$ with a transition matrix $\Pi$ and an invariant measure $\alpha$, the $\alpha$-reversed transition matrix is defined like so: 
$$\Pi^{\alpha}(i, j) = \frac{\alpha(j)}{\alpha(i)} \Pi(j, i)$$
- This matrix is also a stochastic matrix
- If $(X_n)$ is a Markov chain with an initial state $\delta_0$, conditioned on $X_N = 0$, then $Y_n = X_{N - n}$ is a Markov chain with initial distribution $Y_0 = 0$ and transition matrix $\Pi^{\alpha}$, conditioned on $Y_N = \delta_0$
- For such a pair of Markov chains with reversed Transition Matricies, the following holds:
	- If one is recurrent, the other is too
	- If they have the same initial distribution and are stopped at $T_0$, then $(Y_n)_{n = 0}^{T_0}$ has the same distribution as $(X_{T_0 - n})_{n = 0}^{T_0}$
## Convergence
- Given a Markov chain $(X_n)$, that is irreducible, aperiodic and positive recurrent, it will have a unique invariant distribution $\alpha$, for which the following holds:
$$\lim_{n \to \infty} \delta_0 \Pi^n = \alpha$$
- Importantly, this $\delta_0$ does not have to be $\alpha$, instead the Markov chain converges to it's invariant distribution
#### Total Variation
- In order to establish a metric of convergence in the space if distributions on $E$, the total variation is used, which is defined like so:  
$$||\alpha - \beta||_{TV} = \frac12 \sum_{i \in E} |\alpha(i) - \beta(i)|$$