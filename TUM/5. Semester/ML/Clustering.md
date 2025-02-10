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
###### Centroid Initialization
- The first centroid $\mu_1$ is chosen to be a random datapoint
- The rest of the centroids are determined by repeating these steps
1. The minimum $D$ of the distances between all $x_i$ and all determined centroids $\mu_j$ is computed
2. Using this minimum, the next centroid is more likely to be a datapoint which is further away from all the other centroids 
## Gaussian Mixture Model
- The k-means model suffers from sensitivity to outliers and having no uncertainty measure
- A probabalistic approach can be taken instead, in which $p(x, z \mid \theta)$ describes the probability that $x$ belongs to the cluster $z$ given some parameter $\theta$
#### Latent Variables
- The model $p(X \mid \theta)$ can be formulated like so:
$$p(X \mid \theta) = \sum_{Z} p(X, Z \mid \theta) = \sum_{Z} p(X \mid Z, \theta) \cdot p(Z \mid \theta)$$
- Since $Z$ is never observed but just inferred, it is referred to as a latent variable 
#### Model
- In the gaussian mixture model, the prior for the cluster indicators follows a categorical distribution:
$$p(z \mid \theta) = \text{Cat}(\pi)$$
- Here, $\pi$ is a vector of prior probabilities, where $\pi_i$ describes the probability that $z_i = 1$
- The probability of a point belonging to a cluster follows a multivariate normal distribution:
$$p(x \mid z_k = 1, \theta) = \mathcal{N}(x \mid \mu_k, \Sigma_k)$$
- The probability of a single sample can then be described like so:
$$p(x \mid \pi, \mu, \Sigma) = \sum_{k = 1}^K p(z_k = 1 \mid \pi) \cdot p(x \mid z_k = 1, \mu_k, \Sigma_z) = \sum_{k = 1}^K \pi_k \cdot \mathcal{N}(x \mid \mu_k, \Sigma_k)$$
- The log likelihood for the entire dataset thus has this form:  
$$\sum_{i = 1}^N \ln \left(\sum_{k = 1}^K \pi_k \cdot \mathcal{N}(x \mid \mu_k, \Sigma_k) \right)$$
###### Inference
- Ultimately, the optimal parameters $\pi^*, \mu^*$ and $\Sigma^*$ must be determined, so that points can be assigned to clusters
- This can be done via Bayes' theorem:
$$\gamma(z_{ik}) = p(z_{ik} = 1 \mid x_i, \pi, \mu, \Sigma) = \frac{p(z_{ik} = 1 \mid \pi) \cdot p(x_i \mid z_{ik} = 1, \mu_k, \Sigma_k)}{p(x_i \mid \pi, \mu, \Sigma)} = \frac{\pi_k \mathcal{N}(x_i \mid \mu_k, \Sigma_k)}{\sum_{j = 1}^K \pi_j \mathcal{N}(x_i \mid \mu_j, \Sigma_j)}$$
###### Training
- The training of a GMM by optimizing $p(X)$ is usually impossible, which is why the latent variable $Z$ is often introduced and the following expectation is optimized:
$$\mathbb{E}_{Z \sim \gamma_t(Z)} [\ln(p(X, Z \mid \pi, \mu, \Sigma))]$$
- The following two steps are repeated, until the expectation converges:
	1. In the E-step, the prior, in this case the responsibilities $\gamma_t(z_{ik})$ are evaluated, to determine $Z$:
$$\gamma(z_{ik}) = \frac{\pi_k^{(t)} \mathcal{N}(x_i \mid \mu_k^{(t)}, \Sigma_k^{(t)})}{\sum_{j = 1}^K \pi_j^{(t)} \mathcal{N}(x_i \mid \mu_j^{(t)}, \Sigma_j^{(t)})}$$
	1. In the M-step, the parameters $\pi_k^{(t)}, \mu_k^{(t)}, \Sigma_k^{(t)}$ are redetermined:
	$$\mu_k^{(t+1)} = \frac{1}{N_k} \sum_{i = 1}^N \gamma_t(z_{ik})x_i$$
	$$\Sigma_k^{(t + 1)} = \frac 1 N_k \sum_{i = 1}^N \gamma_t(z_{ik}) (x_i - \mu_k^{(t + 1)})(x_i - \mu_k^{(t + 1)})^T$$
	$$\pi_k^{(t + 1)} = \frac{N_k}{N}$$
- In general, the so-called EM algorithm can be applied to different problems