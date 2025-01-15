## Support Vector Machines
- In a typical [[Linear Classification|linear classification]], classes are separated by hyperplanes
- In order to improve classification at the decision boundary, a wide margin around the dividing line can be constructed
#### Constructing the margin
- Two additional and parallel hyperplanes are added to the original one
- When constructing the parallel hyperplanes there must not be samples between them and the original hyperplane
- Since a hyperplane is only defined by its normal vector $w$ and its distance from the origin $b$, the parallel hyperplanes can be constructed by adjusting the bias
- If the original hyperplane is defined by $w^Tx + b = 0$, then the parallel ones are defined by:
$$w^Tx + (b - s) = 0$$
$$w^Tx + (b + s) = 0$$
- The size of the margin can be computed like so:
$$m = \frac{2s}{||w||}$$
###### Constraints
- Let $x_i$ be the $i$th sample, $y_i \in \{-1, 1\}$ the class it is assigned to and let the constraints for the classification be:
$$ w^Tx + b \geq 1, \; \text{if} \; y_i = 1$$
$$ w^Tx + b \leq -1, \; \text{if} \; y_i = -1$$
- These constraints need to hold for a classification to be correct
- In this case the constraints can be condensed to $y_i \cdot (w^Tx + b) \geq 1$
- Additionally, since $s = 1$ this means the margin is $m = \frac{2}{||w||}$
###### Example
![[Pasted image 20250114112112.png]]
#### Optimization Problem
- Let $x_i$ be the $i$th data point, let $i = 1, ..., N$ and $y_i \in \{-1, -\}$ be the class that $x_i$ is assigned to
- In order to determine the hyperplane that classifies the data correctly with the largest possible margin, the following function must be minimized:
$$f_0(w, b) = \frac{1}{2} w^Tw$$
- Additionally, the optimal $w, b$ must always fulfill this constraint:
$$f_i(w, b) = y_i \cdot (w^Tx_i + b) - 1 \geq 0$$
###### Terminology
- The above problem is considered a constrained convex optimization problem
- A point $\theta \in \mathbb{R}^d$ is considered feasable if it satisfies the constraint function, in this case $f_i(\theta) \geq 0$
- The optimal value of the minimization function is called the minimum and the input that produces it is called the minimizer
#### Lagrangian
- Given a constrained convex optimization problem with the minimization function $f_0(\theta)$ and the constraint functions $f_i(\theta) \leq 0$, the Lagrangian is defined like so:
$$L(\theta, a) = f_0(\theta) + \sum_{i = 1}^M a_i f_i(\theta)$$
- Here, $a_i > 0$ is the Lagrange multiplier that is chosen for every data point
- Using this, the Lagrange dual function can be defined as a minimization of the Lagrangian with respect to $\theta$ except that it is unconstrained
$$g(a) = \min_{\theta \in \mathbb{R}^d} \left ( f_0(\theta) + \sum_{i = 1}^M a_i f_i(\theta) \right )$$
- The Lagrange dual function $g(a)$ thus provides the lower bound for the optimal value $p^* = f_0(\theta^*)$ for a given $a$
###### Lagrange Dual Problem
- Another constrained convex optimization problem can be defined using the lagrange dual function
- In this problem, $g(a)$ needs to be maximized, while the constaint that all $a_i \geq 0$ must be fulfilled
- The maximum of this problem can be used to achieve the optimal value $p^* = f_0(\theta^*)$ of the original problem
###### Duality
- The reason why the maximum $d^*$ of the dual Lagrange problem is the minimum $p^*$ of the original optimization is because of the properties of duality between them
- As $g(a)$ is the unconstrained minimum of $L(\theta, a)$, it holds that:
$$d^* \leq p^*$$
- This relationship is called weak duality
- However, under certain conditions, strong duality can be achieved in which case the relationship between $d^*$ and $p^*$ is the following:
$$d^* = p^*$$
###### Complementary Slackness
- Given a solution $\theta^*$ to the original optimization problem as well as $a^*$ to the dual lagrange problem and given that strong dualities between the two solutions holds, the following observation can be made:
$$f_0(\theta^*) = f_0(\theta^*) + \sum_{i = 1}^M a_i^*f_i(\theta^*)$$
$$\rightarrow \sum_i^M a_i^*f_i(\theta^*) = 0$$
$$\rightarrow a_i^*f_i(\theta^*) = 0$$
- This is known as complementary slackness
#### Solving SVM's Primal Problem
- The constrained convex optimization problem can be solved in the following steps:
	1. The Lagrangian must be calculated:
$$L(w, b, a) = \frac{1}{2}w^Tw - \sum_{i = 1}^N a_i(y_i(w^Tx_i + b) - 1)$$
	2. This Lagrangian must be minimized with respect to $w$ and $b$:
$$\nabla_w L(w, b, a) = w - \sum_{i = 1}^N a_i y_i x_i = 0$$
$$\rightarrow w = \sum_{i = 1}^N a_i y_i x_i$$
$$\frac{\mathrm d L}{\mathrm d b} = \sum_{i = 1}^N a_i y_i = 0$$
	3. The second observeration shows that the optimal $w$ is a linear combination of the training samples, and since this $w$ is the minimizer for the Lagrangian with respect to $w$, it can be re-inserted into $L(w, b, a)$ to yield the Lagrange dual function:
$$g(a) = \sum_{i = 1}^N a_i - \frac{1}{2} \sum_{i = 1}^N \sum_{j = 1}^N y_i y_j a_i a_j x_i^T x_j$$
	4. The constraint for the dual Lagrange problem is given by the derivative of $L(w, b, a)$ with respect to $b$:
$$\sum_{i = 1}^N a_i y_i = 0$$
	5. Once this Lagrange dual problem is solved and the optimal $a^*$ is determined, $w$ can be computed using the observation above:
$$w = \sum_{i = 1}^N a_i y_i x_i$$
	6. The bias can be calucated using the complementary slackness property $a_i^*f_i(\theta^*) = 0$ since for every $a_i$ which is not $0$ the following must hold:
$$f_i(\theta^*) = 0$$
$$\rightarrow y_i(w^Tx_i + b) = 1$$
$$\rightarrow b = \frac{1}{y_i} - w^Tx_i$$
#### Support Vectors
- The solving of SVM's primal problem showed, that $w = \sum_{i = 1}^N a_i y_i x_i$ and that $a_i^* f_i(\theta^*) = 0$
- This means that only those $x_i$ for which $a_i \neq 0$ contribute to the actual $w$ 
- Additionally, to uphold complementary slackness, the following must hold for these $x_i$:
$$y_i(w^Tx_i + b) = 1$$
- This means that these $x_i$ lie on the margin of the hyperplane
- Those samples $x_i$ are called support vectors
- Ultimately, most $a_i$ are $0$ which means that there are only the few support vectors are necessary to determine the solution
#### Example
![[Pasted image 20250114110801.png]]
## Soft Margin SVMs
- The above implementation of SVMs only works if the data is linearly separable and there are no noisy samples or outliers 
- If this is not the case, the constraint functions need to be relaxed
#### Slack Variables
- A slack variable $\epsilon_i$ is introduced for every sample $x_i$, which measures how much it violates the margin
- If $\epsilon_i = 0$, it doesn't violate the margin at all, if $0 < \epsilon_i < 1$, then the sample is within the margin but still on the correct side of the hyperplane and if $\epsilon_i > 1$, it is on the wrong side of the hyperplane
- The constraints change accordingly:
$$w^Tx_i + b \geq 1 - \epsilon_i, \; \text{if} \; y_i = 1$$
$$w^Tx_i + b \leq -1 + \epsilon_i, \; \text{if} \; y_i = -1$$
- This can be again condensed to $y_i \cdot (w^Tx_i + b) \geq 1 - \epsilon_i$
- The minimization function for the lagrangian also changes:
$$f_0(w, b, \epsilon) = \frac{1}{2} w^Tw + C \cdot \sum_{i = 1}^N \epsilon_i$$
- Here, $C$ determines how much a violation of the margin is punished during training
###### Solving the Primal Problem with Slack Variables
- To determine the set of support vecotrs, the same steps that were needed to solve the primal problem for SVNs are performed again, except that the Lagrangian has a different form
- This difference in the Lagrangian, however, has little effect on each individual step, since the only change is that the constraint $0 \leq a_i \leq C$ is added to the Lagrange dual function
- As a result, $w$ and $b$ can still be computed by using all samples $x_i$ for which $a_i \neq 0$, i.e. the support vectors: 
$$w = \sum_{i \in S} a_i y_i x_i$$
$$b = \frac{1}{y_i} - w^Tx_i$$
## Kernels
- In order to construct non-linear classifiers, basis functions $\phi$ need to be applied to each sample, in order to make the data linearly separable
- The optimization function for the Lagrange dual function has this form:  
$$g(a) = \sum_{i = 1}^N a_i - \frac{1}{2} \sum_{i = 1}^N \sum_{j = 1}^N a_i a_j y_i y_j x_i^T x_j$$
- This means the basis function $\phi$ needs to be applied to $x_i^Tx_j$, yielding $\phi(x_i)^T\phi(x_j)$
- A kernel function $k(x_i, x_j) = \phi(x_i)^T\phi(x_j)$ can be defined and applied to the Lagrange dual function, which is called a kernel trick:
$$g(a) = \sum_{i = 1}^N a_i - \frac{1}{2} \sum_{i = 1}^N \sum_{j = 1}^N a_i a_j y_i y_j k(x_i, x_j)$$
- After determining the set of support vectors using the approach above, the bias can be computed like this:
$$b = y_i - \left( \sum_{j \in S} a_j y_j k(x_i, x_j)\right)$$
- A new sample can then be classified like this:
$$h(x) = \text{sign} \left( \sum_{j \in S} a_j y_j k(x_j, x) + b\right)$$
#### Kernel Validity
- A kernel is valid, if it produces a symmetric, positive semidefinite kernel matrix $K$ for any input $X$
- A kernel matrix is constructed like this:
$$K = \begin{pmatrix}
k(x_1, x_1) & k(x_1, x_2) & ... & k(x_1, x_N) \\
k(x_2, x_1) & k(x_2, x_2) & ... & k(x_2, x_N) \\
\vdots & \vdots & \ddots & \vdots \\
k(x_N, x_1) & k(x_N, x_2) & ... & k(x_N, x_N) \\
\end{pmatrix}$$
- If a non-valid kernel is used, the problem becomes non-convex and its solution may not be globally optimal
#### Kernel Preserving Operations
- Given two valid kernels $k_1, k_2$, the following kernels are valid as well:
$$k = k_1 + k_2$$
$$k = c \cdot k_1, \; \text{with} \; c > 0$$
$$k = k_1 \cdot k_2$$
$$k(x_1, x_2) = k_1(\phi(x_1), \phi(x_2))$$
$$k(x_1, x_2) = k_1(\phi(x_1), \phi(x_2))$$
$$k(x_1, x_2) = x_1^T A x_2, \; \text{if $A$ is symmetric and positive semidefinite}$$