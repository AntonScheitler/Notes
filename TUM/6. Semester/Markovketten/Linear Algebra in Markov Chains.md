## Transition Probabilities
- Given an initial distribution $\mu$ and the transition matrix $\Pi$ of a Markov chain $(X_n)_{n=0}^{\infty}$, the distribution of $X_n$ can be computed as:
$$\mu^T \Pi^{n}$$
- Additionally, the following holds for the same Markov chain:
$$P(X_{n + m} = j \mid X_n = i) = \Pi^m(i, j)$$
## Properties
- Since $\Pi$ is a stochastic matrix, all of it's Eigenvalues are at most $|1|$
- In fact any $\Pi$ of a Markov Chain has an Eigenvector $\hat{\mu}$, whose Eigenvalue is $1$
- Because of this, the distribution of $\lim_{n \to \infty} X_n = \hat{\mu}$