## K-Means Algorithm
- The k-means algorithm aims to discover a latent structure in a dataset and group datapoint which are similar to each other
#### Model
- In a K-means model, the domain consists of $k$ clusters, which each have a centroid $\mu_k$
- A cluster indicator $z_i \in \{0, 1\}^K$ uses one-hot encoding to convey which cluster a point $x_i$ belongs to
- The K-means objective that must be minimized is described like this:
$$J(X, Z, \mu) = \sum_{i = 1}^N \sum_{k = 1}^K z_{ik} || x_i - \mu_k ||_2^2$$
- Here, each $z_{ik}$ has exactly one value for $k$ which is $1$ due to it's one-hot encoding
- Therefore, to be able to group the datapoints correctly, the optimal cluster centroids and indicators must be found:
$$Z^*, \mu^* = \arg \min_{Z, \mu} J(X, Z, \mu)$$
#### Lloyd's Algorithm
- It is difficult to optimize for both $Z$ and $\mu$ at the same time, which is why they are instead updated in turns via Lloyd's algorithm
###### Steps
- After the centroids have been initialized with $\mu = \{\mu_1, ..., \mu_K\}$, the following steps are repeated until $J(X, Z, \mu)$ converges
	1. The cluster indicators are updated by solving $\min_Z J(X, Z, \mu)$:
	$$z_{ik} = \begin{cases}
	1 \; \text{if} \; k = \arg \min_j ||x_i - \mu_j||_2^2, \\
	0 \; \text{else}
	\end{cases}$$
	1. The cluster centroids are updated by solving $\min_{\mu} J(X, Y, z)$:
	$$N_k = \sum_{i = 1}^N z_{ik}$$
	$$\mu_k = \frac{1}{N_k} \sum_{i = 1}^N z_{ik} x_i$$