## Support Vector Machines
- In a typical [[Linear Classification|linear classification]], classes are separated by hyperplanes
- In order to improve classification at the decision boundary, a wide margin around the dividing line can be constructed
#### Constructing the margin
- Two additional and parallel hyperplanes are added to the original one
- When constructing the parallel hyperplanes there must not be samples between them and the original hyperplane
- Since a hyperplane is only defined by its normal vector $w$ and its distance from the origin $b$, the parallel hyperplanes can be constructed by adjusting the 
- If the original hyperplane is defined by $w^Tx + b = 0$, then the parallel ones are defined by:
$$w^Tx + (b - s) = 0$$
$$w^Tx + (b + s) = 0$$
- The size of the margin can be computed like so:
$$m = \frac{2s}{||w||}$$
###### Constraints
- Let $x_i$ be the $i$th sample, $y \in \{-1, 1\}$ the class it is assigned to and let the constraints for the classification be:
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