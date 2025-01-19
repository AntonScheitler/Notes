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
	4. If the second derivative of the function is positive, it is convex, if it is negative, it is concave
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
## Higher Order Techniques
- Optimization techniques such as gradient descent are considered first order techniques, since they operate only on the first order derivative
- Higher order techniques operate on higher order derivatives
#### Newton Method
- The Newton Method uses the first order and second order derivative of a function in order find its minimum
- Given a starting point $\mathbf{\theta_t}$, the following steps are performed, until a stopping criterium is fulfilled:
	1. The first and second order derivatives of $f(\mathbf{\theta_t})$, i.e. its gradient and Hessian matrix are computed
	2. The point $\mathbf{\theta_{t + 1}}$ is computed: $\theta_{t + 1} = \theta_t - \frac{\nabla f(\theta_t)}{\nabla^2f(\theta_t)}$
	3. This $\theta_{t + 1}$ is the starting point for the next iteration
- Since the Hessian needs to be computed in every iteration, this approach can be quite expensive
## Stochasitc Optimization
- In general, higher-order techniques have great convergence rates but are computationally expensive, especially for high dimensional problems
- This means that first-order techniques are better suited for high dimensional problems
- However, for large scale real-world datasets even first-order techniques can be too expensive, which is why stochastic optimizations are used
#### Stochastic Gradient Descent
 - Given a function $f(\theta) = \sum_{i = 1}^{n} L_i(\theta)$, where $L_i(\theta)$ describes the loss function of a data point given a parameter $\theta$, the expectation of all loss funcations $\mathbb{E}_{j \sim \{1, ..., n\}}[L_j(\theta)]$ can be approximated like this:
$$\mathbb{E}_{j \sim \{1, ..., n\}}[L_j] \approx \frac{1}{|S|} \sum_{j \in S} L_j(\theta)$$
- Here $S \subset \{1, ..., n\}$ is sample smaller than the entire dataset which is used for approximation
- From this, it also follows that $f(\theta)$ can be approximated the same way:
$$f(\theta) = \sum_{i = 1}^n L_i(\theta) \approx \frac{n}{|S|} \sum_{j \in S} L_j(\theta)$$
- This means that instead of an exact gradient, a noisier estimate of it is computed
- Even though the gradient is only estimated, this approach still almost certainly converges to a global minimum
###### Approach
- To perform a stochastic gradient descent, the following steps need to be performed starting with a point $\theta_t$:
	1. A subset $S$  is chosen randomly for every step
	2. The gradient of the estimate of $f$, based on $S$, is computed
	3. The next point of the iteration is calculated: $\theta_{t + 1} = \theta_t - \tau \cdot \frac{n}{|S|} \cdot \sum_{j \in S} \nabla L_j(\theta_t)$
- This is repeated until some stopping criterium is reached
## Distributed Learning
- The learning process can be sped up by distributing the computation load of learning between different machines
- A core challenge in distributed learning is communicating results between machines
#### Types of Parallelism
- In data parallelism, the dataset is divided and distributed across different workers, which all collaborate on a shared parameter server
- In model parallelism, the model is divided and distributed across different workers, which compute their part and merge it into the resulting model
###### Example
![[Pasted image 20241227150349.png]]
![[Pasted image 20241227150402.png]]