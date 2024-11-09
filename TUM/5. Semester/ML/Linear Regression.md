## Regression Problem
- Given a matrix of observations $X = \{x_1, ... x_N\}, \, x \in \mathbb{R}^D$ and a vector of their corresponding targets $y = \{y_1, ..., y_N\}, \, y \in \mathbb{R}$, a function $f$ must be estimated which, maps inputs from targets, so that the following holds:
$$f(x_\text{new}) \approx y_\text{new}$$
#### Example
- The observations may be a set of house areas $x_i$ and their targets are the prices $y_i$
- In this case, each observation vector is one dimensional
![[Pasted image 20241101110124.png]]
## Linear Model
- In a linear model, the target $y$ is produced by a linear function $f$, which has the following form:
$$f_w(x) = w_0 + w_1x_1 + ... + w_Dx_D = w_0 + w^Tx$$
- Here, $w_0$ is the bias can be absorbed by using $\tilde{w} = (w_0, w_1, ..., w_D)$ and $\tilde{x} = (1, x_1, ..., x_D)$ instead of $w$ and $x$ resulting in $f_w(x) = \tilde{w}^T \tilde{x}$
#### Determining $w$
- In order to determine an optimal $w$, the method of least squares can be used
- The following function measures the error, or loss, between the observed data and the output of the model:
$$E_{LS}(w) = \frac{1}{2} \sum_{i = 1}^N (w^Tx_i - y_i)^2$$
- $w$ needs to be chosen, so that this error function is minimal, or in other words:
$$w^* = \arg \min_w E_{LS}(w)$$
- Using the matrix $X$ this can be rewritten like so:
$$w^* = \arg \min_w \frac{1}{2} (Xw - y)^T(Xw - y)$$
- To determine the minimum of the loss, the gradient needs to be computed:
$$\nabla _{w}E_{LS}(w) = X^TXw - X^Ty \stackrel{!}{=}  0$$
- This leads to the normal equation:
$$w^* = (X^TX)^{-1}X^T y = X^{\dagger}y$$
- It holds, that $X^{\dagger} = X^{-1}$, if $X$ is an invertable square matrix
###### Example
![[Pasted image 20241101122901.png]]
## Non-Linear Models
- If the relationship between observations $x$ and targets $y$ is not linear, $f$ needs to be determined differently:
$$f_w(x) = w_0 + \sum_{i = 1}^N w_i \phi_i(x)$$
- This can be generalized to the following form:
$$f_w(x) = w^T \phi(x)$$
- Here $\phi$ can take different forms, depending on the type of the preferred basis function
- This may be $\phi_i(x_j) = x_j^i$ in the case of polynomials or $\phi_j(x) = e^{\frac{-(x - \mu_j)^2}{2s^2}}$ in the case of a gaussian
#### Determining $w$
- The same least-squares method that is used for the linear model can be applied here by changing the corresponding formulae slightly:
$$E_{LS}(w) = \frac{1}{2} \sum_{i = 1}^N (w^T\phi(x_i) - y_i)^2 = \frac{1}{2} (\Phi w - y)^T(\Phi w - y)$$
- Here, $\Phi$ is a matrix with the following shape:
$$\Phi = \begin{pmatrix}
\phi_0(x_1) & \phi_1(x_1) & ... & \phi_N(x_1) \\
\phi_0(x_2) & \phi_1(x_2) & ... & \phi_N(x_2) \\
\vdots & \vdots & ... & \vdots \\
\phi_0(x_N) & \phi_1(x_n) & ... & \phi_N(x_N) \\
\end{pmatrix}$$
- Here $\phi_i: \mathbb{R}^D \rightarrow \mathbb{R}$ is the basis function, where $D$ denotes the number of dimensions in an observation 
- The optimal weights $w^*$ can again be computed like this:
$$w^* = (\Phi^T\Phi)^{-1} \Phi^T y = \Phi^{\dagger}y$$
#### Choosing Degrees
- A regression model may overfit, if the degree of the regression polynomial is too large
- In order to choose the best degree, many approaches are possible
###### Train-Validation
- The standard train-validate split approach works to choose the best degree
- An interesting observation however, is that the overfitting of a model correlates with large weights
###### Regularization
- The least squares approach can be adjusted to use the following formula:
$$E_{\text{ridge}}(w) = \frac{1}{2} \sum_{i = 1}^N (w^T \phi(x_i) - y_i)^2 + \frac{\lambda}{2} ||w||_2^2$$
- Here, $||w||_2^2$ is the squared L2 norm of $w$ and $\lambda$ is the regularization strength
- The larger $\lambda$ is, the smaller the weights $w$ will be
###### Example
![[Pasted image 20241104122158.png]]
#### Bias-Variance Tradeoff
- The error of an estimator can be decomposed into bias and variance
- Those need to be minimized, which can be tricky, since they are conflicting goals ###### Bias
- A high bias usually indicates a rigid model
- This can be caused by high regulations strengths, or misspecification
###### Variance
- A high variance indicates a very sensitive model, which captures a lot of noise during training
- This is often caused by overfitting and the model memorizing the dataset
## Probabalistic Formulation
- In a regression, the goal is to approximate the relationship between an observation and it's target like so:
$$y_i = f(x_i) + \varepsilon_i$$
- This $\varepsilon_i$ is noise and is normally distributed with a fixed precision $\beta$, so that $\varepsilon_i \sim \mathcal{N}(0, \beta^{-1})$
- This means, that the target $y_i$ is normally distributed as well with $y_i \sim \mathcal{N}(f(x_i), \beta^{-1})$
#### Maximum Likelihood
- Since the distribution of a single sample can be described by $p(y_i \mid f_w(x_i), \beta) = \mathcal{N}(y_i \mid f_w(x_i), \beta^{-1})$, the likelihood function for the dataset can be defined like so:
$$p(y \mid X, w, \beta) = \prod_{i = 1}^N p(y_i \mid f_w(x_i), \beta)$$
- Maximizing this likelihood function is equivalent to minimizing the least squares error function
#### Posterior Distribution
- Since the MLE approach can lead to overfitting, the posterior distribution is used
- As described by [[Probabalistic Inference|probabalistic inference]], the postieror is defined like so:
$$p(w \mid X, y, \beta, \cdot) = \frac{p(y \mid X, w, \beta) \cdot p(w \mid \cdot)}{p(y \mid X, \beta, \cdot)}$$
- Here, $p(y \mid X, w, \beta)$ is the likelihood function, $\cdot p(w \mid \cdot)$ is the prior and $p(y \mid X, \beta, \cdot)$ is a normalizing constant
$$p(w \mid X, y, \beta, \cdot) \propto p(y \mid X, w, \beta) \cdot p(w \mid \cdot)$$
###### Determining the Prior
- The prior $p(w \mid \alpha)$ is determined to have an isotropic multivariate normal distribution with a mean of zero:
$$p(w \mid \alpha) = \mathcal{N}(w \mid 0, \alpha^{-1}I)$$
###### Maximum A Posteriori
- Using the prior and the likelihood function, the Maximum A Posteriori estimator can be computed
- Maximizing the MAP estimator is equivalent to a ridge regression, which itself is a regression optimized for the $L2$ Norm
###### Computing the Posterior
- Since both the likelihood function and the prior are gaussian, the posterior is a gaussian as well
- This is because the normal distribution is a conjugate prior to itself
$$p(w \mid \mathcal{D}) = \mathcal{N}(w \mid \mu, \Sigma)$$
- Here, $\mu = \beta \Sigma \Phi^T y$ and $\Sigma^{-1} = \alpha I + \beta \Phi^T \Phi$

#### Prediction
- Predicting the target $y_{\text{new}}$ for a new datapoint $x_{\text{new}}$ can therefore be determined either via a ML estimator, an MAP estimator or the posterior distribution itself
- When using the posterior distribution, the probability that a new datapoint $x_\text{new}$ has a target $y_\text{new}$ is can be computed like this:
$$p(y_\text{new} \mid x_\text{new}, \mathcal{D}) = \int p(y_\text{new} \mid x_\text{new}, w) \cdot p(w \mid \mathcal{D}) \mathrm d w$$