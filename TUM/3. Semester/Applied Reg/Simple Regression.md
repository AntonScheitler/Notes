## Least Squares
- Given a set of points $(x_i, y_i)$, a line needs to be created, which maintains minimal distance to all points
- Therefore, the variables $\hat{\beta_0}, \hat{\beta_1}$ need to be chosen, such that $\sum_{i=1}^{n} (y - y_i)^2$ is minimal, where $y_i = \hat{\beta_0} + \hat{\beta_1}x_i$
#### Solving
- $\hat{\beta_0}, \hat{\beta_1}$ are determined by setting the derivative of $\sum_{i=1}^{n} (y - \hat{\beta_0} - \hat{\beta_1}x_i)^2$ with respect to $\hat{\beta_0}, \hat{\beta_1}$ to $0$ and solving
- The resulting slope and intercept can then be plotted
![[Pasted image 20231113091328.png]]
#### Assumptions
- TODO