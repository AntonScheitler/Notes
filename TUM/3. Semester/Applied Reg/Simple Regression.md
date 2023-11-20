## Least Squares
- Given a set of points $(x_i, y_i)$, a line needs to be created, which maintains minimal distance to all points
- Therefore, the variables $\hat{\beta_0}, \hat{\beta_1}$ need to be chosen, such that $\sum_{i=1}^{n} (y - y_i)^2$ is minimal, where $y_i = \hat{\beta_0} + \hat{\beta_1}x_i$
#### Solving
- $\hat{\beta_0}, \hat{\beta_1}$ are determined by setting the derivative of $\sum_{i=1}^{n} (y - \hat{\beta_0} - \hat{\beta_1}x_i)^2$ with respect to $\hat{\beta_0}, \hat{\beta_1}$ to $0$ and solving
- This is possible because the sum is always positive, meaning that the determined $\hat{\beta}_0, \hat{\beta}_1$ insure that the sum is minimal
- The resulting slope and intercept can then be plotted
![[Pasted image 20231113091328.png]]
#### Assumptions
- In order to perform a proper analysis, certain assumptions need to be made for the dataset
- It is assumed, that the following function applies for every $y$:
$$y = \beta_0 + \beta_1x + \varepsilon, \space \varepsilon \in N(0, \sigma^2)$$
- This means that every $y$ can be approximated with a linear function with some error $\varepsilon$
- The following assumptions apply for each $x$:
	- **Independendence of y:** Each separate observation of a $y$ shoud be independent
	- **Linearity of mean of y:** $\mathbb{E}(\overline{y_0} + \overline{y_1}) = \mathbb{E}(\overline{y_0}) + \mathbb{E}(\overline{y_1})$
	- **Homogeneity of variance of y:** The variance of different samples should be the same
	- **Normal distribution of y:** $y$ should follow a normal distribution