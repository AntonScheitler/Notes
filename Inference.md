## Foundations of Inference
- In inference, one tries to infer the parameters of unknown distributions by taking samples and computing statistics 
- For example, a real-life scenario may have an underlying normal distribution with mean $\mu$ and variance $\sigma^2$, but those parameters aren't actually known
- A statistic is any function $T: X \to \mathbb{R}$, such as the sample mean $\overline{X} = \frac1n \sum_{i = 1}^N X_i$
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
###### Theoretical Approach
- In the theoretical approach, the assumption is made that the sample $X$ follows some distribution, such as the normal or bernoulli distribution
- Using this assumption, the distribution of $T(X)$ can be inferred
- However, such an assumption is only valid if the assumed distribution is likely given the observed data
###### Asymptotic Approach
- The central limit theorem is foundational to the asymptotic approach and states the following: 
- If $X_1, ..., X_n$ is a series of independent, indentically distributed random variables with mean $\mu$ and variance $\sigma^2$, then the sample mean $\overline{X} = \frac1n \sum_{i = 1}^n X_i$ will follow a normal distribution with mean $\mu$ and variance $\frac{\sigma^2}{n}$, as $n \to \infty$
- This means that with enough samples, the actual mean $\mu$ and variance $\sigma^2$ of the underlying distribution of $X_1, ..., X_n$ can be determined
###### Bootstrap Approach
- In the bootstrap approach, given a sample $X_1, ..., X_n$ and a number of resamples $B$, the drawing of multiple samples is simulated like so
	1. For every $b = 1, ..., B$ n random observations are selected from $\{X_1, ..., X_n\}$ with replacement to create a resample $X^b = \{X_1^b, ..., X_n^n\}$
	2. For every resample, the statistic $T(X^b)$ can be computed
	3. These $T(X^b)$ statistics can be used to infer information about the sampling distribution, e.g. via the sample mean or sample variance
## Confidence Intervals
- Point estimates for parameters $\theta$ are often incorrect, as they are the results of statistics which follow a sampling distribution with non-zero variance, as shown above
- Instead, confidence intervals with an error level $\alpha$ are defined in which the parameter $\theta$ lies with a probability of $1 - \alpha$
- For computing the confidence intervals, the methods from before can be used
#### Theoretical Approach
- If the distribution of the underlying data is given or can be assumed with high probability, the properties of the statistic can be used in order to infer a confidence interval
#### Asymptotic Approach
- Given enough samples, it is known that the distribution of the sample mean follows a normal distribution with mean $\theta$ and variance $\frac{\sigma^2}{n}$
- Using this, a confidence interval of $1 - \alpha$ can be constructed by:
$$T(X) \underline{+} z_{1 - \alpha/2} \cdot \text{SE}(T(X))$$
- Here, $SE(T(X))$ is the standard error of $T(X)$ and $z_{1 - \alpha/2}$ is the $1 - \alpha/2$ quantile of $\mathcal{N}(0, 1)$, meaning that $P(x < z_{1 - \alpha/2}) \leq 1 - \alpha/2$
#### Bootstrap Approach
- There's different ways to construct a confidence interval if the bootstrap approach is used
###### Percentile Method
- Since every element in a bootstrap distribution $T(X^b$) is an estimator for the population parameter $\theta$, computing a $100(1 - \alpha)$% confidence interval simply means setting the boundaries of the distribution so that they include only the middle $100(1 - \alpha)$% elements
- This means the $\alpha/2$ percentile is the left boundary and the $1 - \alpha/2$ percentile is the right boundary
###### Standard Error Method
- If the sample distribution is symmetrical, the same procedure as in the asymptotic approach can be used:
$$\overline{X} \underline{+} z_{1 - \alpha/2} \cdot \text{SE}(T(X^b))$$
- Here, the $\overline{X}$ denotes the sample mean and $\text{SE}(T(X^b))$ the standard error of the sample distribution