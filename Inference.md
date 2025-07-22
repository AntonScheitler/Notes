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
- For example, if the data follows a normal distribution with unknown mean $\theta$ and known variance $\sigma^2$, a $100(1 - \alpha)$% confidence interval can be constructed like this:
$$\overline{X_n} \underline{+} z_{1 - \alpha / 2} \cdot \frac{\sigma}{\sqrt{n}}$$
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
## Hypothesis Testing
- A hypothesis is always build around a null-hypothesis $H_0$ which represents the claim that there is no underlying causality or correlation and all observations are essentially random 
- In a statistical test, a sample $X_1, ..., X_n$ is evaluated using a test statistic $T(X)$ in order to decide of $H_0$ can be rejected
#### Errors
- A type 1 error occurs, when rejecting $H_0$, when in reality $H_0$ holds, which happens with the probability of the significance level $\alpha$
- A type 2 error occurs, when not rejecting $H_0$, when in reality $H_0$ doesn't hold, which happens with probability $\beta$ 
###### Power of a Test
- The power of a test is the probability with which it correctly rejects $H_0$, i.e. $1 - \beta$
- In order to determine the minimum size of a sample so that a given test, like a t test, has a power of at least `pow`, the following R function can be used:
```
power.t.test(
	delta = d, 
	sd = s,
	sig.level = 0.05,
	power = pow,
	type = "one.sample",
	alternative = "one.sided"
)
```
- Here, `delta` refers to the effect size, which is a measure of strength of the relationship of two variables
#### P-Value
- The p-value quantifies the strength of evidence to reject $H_0$
- If the p-value falls below some predefined significance level $\alpha$, such as $0.05$ or $0.01$, then $H_0$ can be rejected
###### Two-Sided v. One-Sided Alternatives
- The alternative hypothesis $H_A$ to $H_0$, can be either one-sided or two sided
- In a one sided hypothesis, the two hypothesis look like so:
$$H_0: \theta = \theta_0 \; \; H_A: \theta \neq \theta_0 $$
- In a two sided hypothesis, the two can have either one of the following forms:
$$H_0: \theta = \theta_0 \; \; H_A: \theta < \theta_0 $$
$$H_0: \theta = \theta_0 \; \; H_A: \theta > \theta_0 $$
#### Theoretical Approach
- If the underlying distribution of the data is known, then tests specific to that distribution can be used
###### Binomial Test
- To test if a random variable adheres to a bernoulli distribution with some success probability $q$, a binomial test can be performed:
```
binomial.test(x = num_success, n = num_total, p = q, alternative = "two.sided")
```
###### T Test
- To test if the mean of some normally distributed random variable is above or below some value $\theta$, a t test can be used: 
```
t.test(data_col, mu = theta, alternative="less")
```
#### Asymptotic Approach
- The asymptotic approach uses the Central Limit theorem in order to create tests
###### Proportion Test
- To test if a proportion of successes follows a certain percentage $q$, the following test can be done:
```{r}
prop.test(x = num_success, n = num_total, p = q, alternative = "two.sided", correct = FALSE)
```
- This is very similar to the binomial test in the theoretical approach, except that we don't expect the sum of successes to follow a binomial distribution and instead only use the CLT
###### Chi-Squared Test
- A Chi-Squared Test can be used to determine if two variables are independent of each other
- $H_0$ for such a test states that the variables are independent 
- A Chi-Squared Test is computed like this:
$$\chi^2(X, Y) = \sum_{i = 1}^k \sum_{j = 1}^l \frac{(N_{ij}(X, Y) - E_{ij}(X, Y))^2}{E_{ij}(X, Y)}$$
- Here, given that $X$ and $Y$ are categorical variables, with lables $u_1, ... u_k$ and $v_1, ... v_j$, $N_{ij}(X, Y)$ is the sum of the $i$th row and $j$th column of the contingency table of $X$ and $Y$
- $E_{ij}(X, Y)$ on the other hand is defined as:
$$E_{ij}(X, Y) = \frac{N_i(X, Y) \cdot N_j(X, Y)}{N(X, Y)}$$
- Here, $N_i$ is the sum of the $i$th row, $N_j$ that of the $j$th column and $N$ that of the entire table
- A Chi-Squared Test of two variables can be performed like this in R:
```{r}
chisq.test(col1, col2)
```
#### Simulation-Based Testing
- In simulation based testing, the observed scenario is simulated a number of times under the assumption of $H_0$, i.e. that some variable follows a certain distribution with a certain parameter
- The results of the simulations are then compared to the observed scenario in order to see how many of them deviated as much as the observation
- These simulations can be carried out in R like so:
```{r}
df |>
    specify(response = response, success = "correct") |>
    hypothesize(null = "point", p = 1/3) |>
    generate(reps = 1000, type = "draw") |>
    calculate(stat = "prop")
```
- Here, the null parameter of hypothesize can take either "point", in which case an appropriate parameter must be specified, or "independence"
###### Bootstrap Method
- Bootstrap samples can also be taken in order to perform a simulation-based test
- However, bootstrap samples aren't created from just taking samples from the observation with replacement, but instead, the observation is permuted like this:
$$x_i^* = x_i - \overline{x} + \theta_0$$
- Where $\theta_0$ is the mean under $H_0$
- This way, the bootstrap samples adhere to $H_0$, while still preserving their variance 
## Inference for Linear Regression
- Hypothesis testing can also be applied to a linear regression
- More specifically, one can formulate a test problem in which $H_0$ states that the slope of one variable has a certain value, i.e. $\beta_j = \beta_{j, 0}$ and $H_A$ states the opposite, i.e. $\beta_j \neq \beta_{j, 0}$
- In many scenarios, $H_0$ states there's no relation, meaning that $\beta_{j, 0} = 0$
#### Theoretical Approach
- It is assumed that the irreducible errors $\epsilon_0$ are independent and follow a normal distribution with mean $0$ and some variance $\sigma^2$
- A so-called t-statistic for the $j$th slope can be constructed like this:
$$T_j(y, X) = \frac{\hat{\beta}_j(y, X) - \beta_{j, 0}}{{\text{SE}_{\hat{\beta}_j}}(y, X)}$$
- Here, $\hat{\beta}_j$ is the least-squares estimate and $\text{SE}_{\hat{\beta}_j}$ it's estimated standard error
- This statistic has $n - (k + 1)$ degrees of freedom where $n$ is the number of datapoints and $k$ is the number of explanatory variables
#### Simulation-Based Approach
- Since $H_0$ states that there's on relation between an explanatory variable $x_j$ and the response variable, a simulation based approach can be constructed by permuting this $x_j$ and keeping all the other predictors the same
- The idea is that if the response variable is truely independent of $x_j$, then randomly permuting it won't change the resulting fit of the regression model
- One can then check if the observed fit is an outlier compared to the fits of the generated data
- In R this can be done like so:
```{r}
observed_fit <- data |>
  specify(response ~ exp1 + exp2) |>
  fit()

null_fits <- data |>
  specify(response ~ exp1 + exp2) |>
  hypothesize(null = "independence") |>
  generate(reps = 1000, type = "permute", variables = c(exp1, exp2)) |>
  fit()

null_fits |>
  get_p_value(observed_fit, direction = "two-sided")
```
#### Residual Analysis
- In order to perform a proper inference of a linear regression model, the following conditions must hold:
	- Each variable is linearly related to the outcome
	- Residuals have constant variability
	- Residuals follow a normal distribution 
###### Leverage Score
- The leverage score of an observation is the $i$th diagonal entry of the hat matrix $H$ which is defined by:
$$H = X(X^TX)^{-1}X^T$$
- This score assumes values between $0$ and $1$ and describes the influence that the $i$th observation has on the $i$th fitted value.
- If there's a sudden jump in the leverage score from some observations to others, then it's likely that those are outliers
###### Cook's Distance
- The Cook's distance $D_i$ is a measure based on the leverage score of a variable and indicates how influencial an observation is overall 
- In general, if $D_i > 0.5$ or $D_i > 1$ then an observation is considered influencial