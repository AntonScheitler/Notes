## Least Squares
- Given a set of points $(x_i, y_i)$, a line needs to be created, which maintains minimal distance to all points
- Therefore, the variables $\hat{\beta_0}, \hat{\beta_1}$ need to be chosen, such that $\sum_{i=1}^{n} (y - y_i)^2$ is minimal, where $y_i = \hat{\beta_0} + \hat{\beta_1}x_i$
#### Solving
- $\hat{\beta_0}, \hat{\beta_1}$ are determined by setting the derivative of $\sum_{i=1}^{n} (y - \hat{\beta_0} - \hat{\beta_1}x_i)^2$ with respect to $\hat{\beta_0}, \hat{\beta_1}$ to $0$ and solving
- This is possible because the sum is always positive, meaning that the determined $\hat{\beta}_0, \hat{\beta}_1$ insure that the sum is minimal
- The resulting slope always passes through the data centroid $(x_i, y_i)$ and can be plotted
![[Pasted image 20231113091328.png]]
#### Assumed Model
- In order to perform a proper analysis, certain assumptions need to be made for the dataset
- It is assumed, that the following function applies for every $y$:
$$y = \beta_0 + \beta_1x + \varepsilon, \space \varepsilon \in N(0, \sigma^2)$$
- This means that every $y$ can be approximated with a linear function with some error $\varepsilon$
- The following assumptions apply for each $x$:
	- **Independendence of y:** Each separate observation of a $y$ shoud be independent
	- **Linearity of mean of y:** $\mathbb{E}(\overline{y_0} + \overline{y_1}) = \mathbb{E}(\overline{y_0}) + \mathbb{E}(\overline{y_1})$
	- **Homogeneity of variance of y:** The [[Statistical Basics|variance]] of different samples should be the same
	- **Normal distribution of y:** $y$ should follow a normal distribution
#### Expectation of Parameters
- In this model, $\beta_0$ and $\beta_1$ are the population values and $\hat \beta_0$, as well as $\hat \beta_1$ are the estimated values based on the dataset
- In order to proof that the calculated $\hat{\beta_1}$ and $\hat{\beta_0}$ are representative, it needs to be shown, that they are [[Statistical Basics|unbiased]]
- Therefore the following needs to be proven using the properties of the [[Statistical Basics|expectation]]:
$$E(\hat\beta_0) = \beta_0$$
$$E(\hat\beta_1) = \beta_1$$
#### Variance of the slope
- Using the [[Statistical Basics|arithmetic properties of the variance]], the variance of $\hat \beta_1$ can be derived to be $\frac{s^2}{\sum_{i=1}^n (x_i - \overline{x})^2}$, where $s$ is an unbiased estimate for $\sigma$
- The standard error of the slope is therefore:
$$se(\hat \beta_1) = \sqrt{Var(\hat \beta_1)} = \frac{s}{\sqrt{\sum_{i=1}^n (x_i - \overline x)^2}}$$
## Maximum Likelihood
- Alternatively to the least squares approach, the parameters $\hat\beta_0$ and $\hat\beta_1$ can be obtained by maximizing a likelihood function
#### Likelihood function
- Given a set of parameters, the likelihood function describes the probability of set of data points
- This function needs to be maximized, such that the observed data points are most probable
$$L = \prod_{i=1}^n \frac{1}{\sqrt{2 \pi \sigma^2}} \exp \big (- \frac{1}{2\sigma^2}(y_i - \beta_0 - \beta_1x_i)^2 \big )$$
## T-Tests
- In order to show, that the results are [[Statistical Basics|statistically significant]], they are compared to the null hypothesis
- The t-statistic measures how far a computed result is from it's hypothesized null value in units of the standard error
- A value $\alpha$ represents a threshold, past which the null hypothesis can be rejected
#### Null Hypothesis
- The null hypothesis states that there is no correlation in the given dataset and, under this model, the slope has a value of $0$
#### Quantile Approach
- A normal distribution represents the values, the slope can assume
- If the computed slope is in one of the $\frac{\alpha}{2}$ quantiles, the result is statistically significant
###### Example
![[Pasted image 20231205092621.png]]
#### Probability Approach
- A p-value represents the probability of observing the computed slope under the null hypothesis
- If the p-value is then below a certain $\alpha$ threshold, the null hypothesis can be rejected
###### Example
![[Pasted image 20231205092852.png]]
## Prediction
- Using the assumed model, predictions can be made about where the mean of a population at a given $x$ lies and where a new datapoint at a given $x$ may lie
- A confidence interval describes how large an interval has to be, for a prediction to meet a certain likelihood
- In general, the confidence interval of the two predictions is centered around the same location, with the CI of the datapoint prediction being wider than that of the mean prediction
#### Prediction of the mean
- The confidence interval for the prediction of the mean can be computed using the [[Statistical Basics|variance]] of the [[Statistical Basics|expectation]] of the assumed model
#### Prediction of a new point
- The confidence interval for the prediction of a new point is computed via the variance of the model
## Analysis of variance
- In an analysis of variance, a variable is partitioned into components attributable to different sources of variation
- The partitioned groups need to have a low variance and distinct expectations, in order to be considered a probable source of variation
#### Example
- The weight of dogs in a dogshow has a large variation, which can have different causes
- Partitioning the dogs in groups of young and old, as well as short- and long-haired, leads to a poor fit, since the variance is great and the expectations are similar:
![[Pasted image 20231212094243.png]]
- Partitioning the dogs by their breed, however leads to a better fit:
![[Pasted image 20231212094326.png]]
- Therefore, the breed of a dog is a probable source of weight differences in the dog dataset
## Percent Variation
- TODO