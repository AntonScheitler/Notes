## General
- Many machine learning tasks are optimization problems, such as minimizing the error in a linear regression or maximizing the likelihood in a linear classification
- Those optimization problems revolve around some parameter $\theta$ which has to be learned
- Determining this parameter can rarely be done using closed form solutions
- Instead, different optimization methods are used
#### Formulation
- If $\mathcal{X}$ is the domain, i.e. possible values for $\theta$ and $f(\theta)$ is the function which needs to be optimized, then any optimization problem can be formulated like so:
$$\theta^* = \arg \min_{\theta \in \mathcal{X}} f(\theta)$$
- The optimized parameter $\theta^*$ is therefore the global minimum of $f(\theta)$
- Determining this global minimum is therefore the objective in an optizmization
- Finding this minimum is often not as simple as computing the gradient and solving for $0$, since the number of parameters can be very large
## Convexity
- A domain is convex if and only if it holds that a line drawn between any two points in the domain is contained in the domain as well
- More formally, for all $x, y \in X$ it must hold that $\lambda x + (1 - \lambda) y \in X$ for $\lambda \in [0, 1]$
#### Convex Functions
- A function is convex if the domain that consists of all points above and on a function is convex
- This can also be expressed like so:
$$\forall \; x, y \in X: \lambda f(x) + (1 - \lambda)f(y) \geq f(\lambda x + (1 - \lambda)y), \; \text{for} \; \lambda \in [0, 1]$$
- If a function is convex, it has no local minima and only global ones, which makes optimization a lot more simple
###### First Order Convexity
- The difference between two values $f(x)$ and $f(y)$ is always bounded by function values between $x$ and $y$
- This fact can also be described like this:
$$f(y) - f(x) \geq (y - x)^T \nabla f(x)$$
###### Verifying Convexity
- One of the following steps needs to be followed to prove, that a function is convex:
	1. It can be shown that the definition of convex functions holds 
	2. A fact about convex functions, such as first order convexity, can be exploited
	3. It can be shown that a given function can be obtained by combining simple convex functions with operations that preserve convexity 
###### Convexity Preserving Operations
- If $f_1$ and $f_2$ are convex functions and $g$ is a concave function, then a convex function $h$ can be created like this:
$$h(x) = f_1(x) + f_2(x)$$
$$h(x) = \max(f_1(x), f_2(x))$$
$$h(x) = c \cdot f_1(x), \text{if } c \geq 0$$
$$h(x) = c \cdot g(x), \text{if } c \leq 0$$
$$h(x) = f_1(Ax + b)$$
$$h(x) = m(f_1(x)), \text{if} \; m \; \text{is convex and non-decresing}$$
###### Example
![[Pasted image 20241125135355.png]]
#### Problems
- Even if a function is convex, there may still be problems that arise when trying to compute the minimum
- For example, the gradient may not be computable, lay outside the domain or the function may not be differentiable on the whole domain 
#### Example
![[Pasted image 20241125135343.png]]
## Gradient Descent
- Gradient descent is an approach which iteratively computes gradients to approximate the minimum of a function
#### Iteration
- Given a starting point $\theta$ the following three steps are repeated, until a stopping criterion is satisfied:
	1. The gradient at $\theta$ is computed: $\Delta \theta = - \nabla f(\theta)$
	2. The length $t$ to descent the gradient is chosen in a line search: $t^* = \arg \min_{t > 0} f(\theta + t \cdot \Delta \theta)$
	3. The reached point is chosen as the starting point for the next iteration: $\theta = \theta + t^* \cdot \Delta \theta$
- Often, parallel computations can be used to accelerate the computation of the gradient but the line search remains expensive
- To speed up line search, one picks a learning rate $\tau$ before executing the gradient descent
- This $\tau$ will then be used as the length $t$ in the iteration process above
- Now the line search can be skipped, which speeds up the descent
###### Learning Rate Considerations
- A few considerations need to be made when picking the learning rate
- If $\tau$ is too small the convergence will be very slow and the descent may terminate in a local minimum
- If $\tau$ is too large the descent oscillates too much and the descent may never terminate at all
###### Types of Learning Rates
- The learning rate can be changed dynamically which supports different strategies:
	- $\tau$ may decrease as the descent continues in order to achieve fine-tuning in the later stages of the iteration
	- A momentum variable can be used so that the search accelerates as long as the gradients point in the same direction
	- $\tau$ may be different for different parameters and smaller if the gradient happens to be very large