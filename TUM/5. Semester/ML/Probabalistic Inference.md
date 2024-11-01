## Maximum Likelihood
- When observing a probabalistic phanomenon, the underlying probabilities are unknown
- In order to estimate those probabilities, one can use the maximum likelihood estimator
#### Application
- Consider a series of $10$ coinflips, which yield $\text{H T H H T H H H T H}$, where $\mathrm{H}$ represents heads and $\mathrm{T}$ tails respectively
- The underlying probability of a coinflip resulting in tails is unknown and will be represented by $\theta$ 
- Assuming all flips are independent and identically distributed, the probability of this series of coinflips being observed can be described with this likelihood function:
$$p(\text{H T H H T H H H T H} \mid \theta) = \prod_{i = 1}^{10}p(F_i = f_i \mid \theta) = \theta^3 (1 - \theta)^7$$
###### Approximating $\theta$
- In order to derive a good approximation for $\theta$, the likelihood function must be maximized
- Therefore it's derivative is taken, set to $0$ and solved for $\theta$
- In most cases computing $\theta$ this way is complicated, which is why the logarithm of the likelihood function is being used
## Bayesian Inference
- The observation that forms the basis of a maximum likelihood estimation may not be entirely representative
- A prior distribution $p(\theta)$ is used to represent a belief or an expectation on the behavior of $\theta$
- This prior distribution needs to fulfill certain criteria:
	- It must not depend on the data
	- $p(\theta) > 0$ for all $\theta$
	- $\int p(\theta) \, \mathrm{d}\theta = 1$
#### Bayes Formula
- Using the prior $p(\theta)$ and the then observed data $\mathcal{D}$, the posterior distribution $p(\theta \mid \mathcal{D})$ can be computed:
$$p(\theta \mid \mathcal{D}) = \frac{p(\mathcal{D} \mid \theta) \cdot p(\theta)}{p(\mathcal{D})}$$
- Here, $p(\mathcal{D} \mid \theta)$ is the likelihood and $p(\mathcal{D})$ is the evidence, which serves to normalize the posterior
- This evidence can be computed using the likelihood and prior:
$$p(\mathcal{D}) = \int p(\mathcal{D} \mid \theta) p(\theta) \mathrm{d}\theta$$
- The posterior distribution is therefore the result of the prior and likelihood
###### Example
![[Pasted image 20241023175808.png]]
## Maximum A Posteriori
- Similar to a maximum likelihood estimation, a MAP chooses $\theta$, so that it maximizes the likelihood of the posterior distribution
- This behavior can be expressed like so:
$$\theta_{MAP} = \arg \max_\theta p(\theta \mid \mathcal{D}) = \arg \max_\theta \frac{p(\mathcal{D} \mid \theta) \cdot p(\theta)}{p(\mathcal{D})} = \arg \max_\theta p(\mathcal{D} \mid \theta) \cdot p(\theta)$$
#### Approximating $\theta_{MAP}$
- The likelihood function has already been established to look like this:
$$p(\mathcal{D} \mid \theta)  = \theta^{|T|} \cdot (1 - \theta)^{|H|}$$
- The prior distribution is chosen to have this form:
$$p(\theta) = \frac{\Gamma(a + b)}{\Gamma(a) \cdot \Gamma(b)} \cdot \theta^{a - 1}(1 - \theta)^{b - 1}$$
- The posterior can be rewritten this way:
$$p(\theta \mid \mathcal{D}) = \frac{p(\mathcal{D} \mid \theta) \cdot p(\theta)}{p(\mathcal{D})} \propto p(\mathcal{D} \mid \theta) \cdot p(\theta)$$
- Inserting the likelihood and prior yields:
$$p(\theta \mid \mathcal{D}) = \theta^{|T|} (1 - \theta)^{|H|} \cdot \frac{\Gamma(a + b)}{\Gamma(a) \cdot \Gamma(b)} \theta^{a - 1}(1 - \theta)^{b - 1} = \theta^{|T| + a - 1}(1 - \theta)^{|H| + b - 1}$$
- Since we need to determine $\theta_{MAP} = \arg \max_{\theta} p(\theta \mid \mathcal{D})$, we apply $\log$ and solve for $0$ to obtain:
$$\theta_{MAP} = \frac{|T| + a - 1}{|H| + |T| + a + b - 2}$$
## Estimating the Posterior
- Using MAP just yields the most probable value for $\theta$ under the posterior distribution
- In order to determine the expectation of $\theta$, or it's variance, the posterior distribution itself needs to be determined
- The following holds for the posterior:
$$p(\theta \mid \mathcal{D}) \propto p(\mathcal{D} \mid \theta) \cdot p(\theta) =\theta^{|T| + a - 1}(1 - \theta)^{|H| + b - 1}$$
#### Normalizing the posterior
- The postierior is not normalized, however, it bears some resemblance to the Beta distribution, which is normalized: 
$$\frac{\Gamma(a + b)}{\Gamma(a) \cdot \Gamma(b)} \theta^{a - 1}(1 - \theta)^{b - 1}$$
- Therefore, to normalize the posterior distribution it needs to be mulitplied with the following constant:
$$\frac{\Gamma(|T| + a + |H| + b)}{\Gamma(|T| + a) \cdot \Gamma(|H| + b)}$$
- The posterior thus assumes the Beta distribution:
$$p(\theta \mid \mathcal{D}) = \mathrm{Beta}(\theta \mid |T| + a, |H| + b)$$
#### Conjugate Priors
- The reason why the posterior and prior are in the same family of distributions is because the distribution of the prior is a conjugate prior to that of the likelihood 
- In this case specifically, the Beta distribution of the prior is a conjugate prior to the Bernoulli distribution of the likelihood, resulting in the posterior followig the Beta distribution
- If a non-conjugate prior had been chosen, then the posterior and $\theta_{MAP}$ would not have a closed form
## Predicting Coin Flips
- When using the maximum likelihood, or the maximum a posteriori approach the likelihood of a coinflip being tails is simply $\theta_{MLE}$, or $\theta_{MAP}$
- When using the esitmated posterior distribution, the probability of a flip being tails is provided by the posterior predictive distribution:
$$p(\text{flip is } f \mid \mathcal{D}, a, b)$$
- Here, $\mathcal{D}$ are the observations and $a$ and $b$ are the parameters of the prior distribution and $f = \{0, 1\}$ represents the possible results
#### Determining the Posterior Predictive Distribution
- This posterior predictive distribution is computed like this:
$$p(f \mid \mathcal{D}, a, b) = \int_0^1 p(f \mid \theta) \cdot p(\theta \mid \mathcal{D}, a, b) \mathrm d \theta$$
- Inserting the already known forumulae $p(f \mid \theta) = \theta^f (1 - \theta)^{1 - f}$ and $p(\theta \mid \mathcal{D}, a, b) = \text{Beta}(\theta \mid |T| + a, |H| + b)$ yields:
$$p(f \mid \mathcal{D}, a, b) = \frac{(|T| + a)^f(|H| + b)^{(1 - f)}}{|T| + a + |H| + b} = \text{Ber}\left ( f \, \Bigg | \, \frac{|T| + a}{|T| + a + |H| + b} \right )$$
- This approach is considered the fully Bayesian analysis