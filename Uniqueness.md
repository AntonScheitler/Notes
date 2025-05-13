## Uniqueness in Distribution
- Given a state space $E$, a distribution $\mu$ over $E$, a stochastic matrix $\Pi$ and a stochastic process $(X_n)_{n \in \mathbb{N}_0}$ the following three statements are equivalent:
	1. $(X_n)_{n \in \mathbb{N}_0}$ is a Markov chain
	2. $$\forall n \in \mathbb{N}_0, \:i_0, ..., i_n \in \mathbb{N}_0: P(X_0 = i_0, ..., X_n = i_n) = \mu(i_0) \cdot \prod_{k = 2}^n \Pi(i_{k-1}, i_{k})$$
	3. $$A_0, ..., A_n \subseteq E: P(X_0 \in A_0, ..., X_n \in A_n) = \sum_{i_0 \in A_0} \mu(i_0) \cdot \; ... \; \cdot \sum_{i_n \in A_n} \Pi(i_{n-1}, i_n)$$
- If any two Markov chains $(X_n)_{n \in \mathbb{N}_0}$ and $(Y_n)_{n \in \mathbb{N}_0}$ have the same initial distribution $\mu$ and transition matrix $\Pi$, the distributions of $(X_n)$ and $(Y_n)$ are identical