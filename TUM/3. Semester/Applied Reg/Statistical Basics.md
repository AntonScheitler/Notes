## Random Variable
- A random variable is a function, which a set of outcomes
- Each of those outcomes has a certain probability
#### Example
- A random variable might be the number of heads in a series of three coin tosses
- The outcomes with their probability in this case would look like this:
![[Pasted image 20231120195334.png]]
## Expectation
- The expectation $E$ of a random variable is it's weighted average, meaning that it is the sum of all outcomes, multiplied by their probability of occuring
- The expectation $E$ is therefore the outcome, a random variable is expected to have, though since it is an arithmetic expression it may not actually be a vaild outcome
#### Example
- Given a random variable $X$, which is the number of heads in a series of three coin tosses, the expectation is:
$$E(X) = 0 + \frac{3}{8} + 2 \cdot \frac{3}{8} + 3 \cdot \frac{1}{8} = \frac{3}{2}$$
#### Arithmetic Properties
- TODO
## Bias
- Bias is the difference between an estimated value based on a sample and the true value based on the entire population
- An estimated value $\hat{\Theta}$ is unbiased, if it's expectation $E(\hat{\Theta})$ is equal to the true value $\Theta$
- In general, since the true value is never known for certain, certain assumptions are made regarding $\Theta$ to approximate a true value 
## Variance
- The variance $\sigma^2$ is the expectation of a dataset's deviation from the mean squared
- It therefore measures, how dispersed a dataset is
#### Example
- Given a random variable $X$, which is the number of heads in a series of three coin tosses, variance is:
$$Var(X) = E[(X - E(X))^2] = \left(0 - \frac{3}{2}\right)^2 \cdot \frac{1}{8} + \left(1 - \frac{3}{2}\right)^2 \cdot \frac{3}{8} + \left(2 - \frac{3}{2}\right)^2 \cdot \frac{3}{8} + \left(3 - \frac{3}{2}\right)^2 \cdot \frac{1}{8} = \frac{3}{4}$$
#### Arithmetic Properties
- TODO
## Standard error
- Another measure for the dispersion of a dataset is the standard error $se$
- The standard error is defined to be the square root of the variance
#### Example
- Given a random variable $X$, which is the number of heads in a series of three coin tosses, standard error is:
$$se(X) = \sqrt{Var(X)} = \sqrt{\frac34}$$
## Covariance
- The covariance of two variables $X$ and $Y$ measures their joint variability
- The sign of the covariance describes if the variables are proportional or inversely proportional to one another
- A covariance of 0 means that the variables don't correlate at all
- Mathematically, covariance is described as:
$$cov(X, Y) = E \big ((X - E(X)) \cdot (Y - E(Y)) \big )$$
#### Arithmetic properties
- TODO