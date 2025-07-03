## Foundations of Inference
- In inference, one tries to infer the parameters of unknown distributions by taking samples and computing statistics 
- For example, a real-life scenario may have an underlying normal distribution with mean $\mu$ and variance $\sigma^2$, but those parameters aren't actually known
- A statistic might be the sample mean $\overline{X} = \frac1n \sum_{i = 1}^N X_i$
#### Bias and Standard Error
- The bias of a statistic $T(X)$ is it's tendency to over-/underestimate a true parameter $\theta$ and is defined as:
$$\mathbb{E}[T(X)] - \theta$$
- The standard error of $T(X)$ is then defined as:
$$\text{SE}(T(X)) = \sqrt{\text{Var}(T(X))}$$
- The sample mean and sample variance can be computed as follows:
$$\overline{X} = \frac{1}{n} \sum_{i = 1}^n X_i, \; \; S^2 = \frac{1}{n - 1}\sum_{i = 1}^n(X_i - \overline{X})^2$$
#### Sampling Distribution
- Given a sample $(X_1, ..., X_n)$ and a statistic $T(X)$, the distribution of $T(X)$ is called a sampling distribution
- Ideally in order to properly approximate the sampling distribution, one would take a sample multiple times, which is rarely possible in reality
- Different approaches are used to compensate for this