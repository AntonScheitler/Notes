## Neural Networks
- A [[Linear Classification|classification]] problem can be represented by a graph in which nodes are inputs and edges are weights that are applied to them
- Many classification problems, however, cannot be solved with just one layer of inputs and weights
- By placing multiple layers of inputs and weights after one another, a neural network can be created
- Every layer that is neither the input nor the output layer, i.e the first or last layer, is considered a hidden layer
#### Feed-Forward Network
- If every layer of a network only connects to the next layer and never itself or previous layers, the network is considered a feed-forward neural network 
#### Universal Approximation Theorem
- The universal approximation theorem states that any continuous function over a closed and bounded subset of $\mathbb{R}^D$ can be approximated by a neural network with just one hidden and one output layer
#### Layer Construction
- Some datasets cannot be linearly separated, in which case a simple linear classification algorithms will fail
- To address this, a transformation function $\phi$ can be applied to the data, which makes it linearly separable:
$$f(x, w) = \sigma \left ( w_0 + \sum_{j = 1}^{M - 1} w_j \phi_j(x) \right ) = \sigma(w^T \phi(x))$$
- Here, $w_0$ represents the bias, $w_j$ the weights and $\sigma$ the activation function of a layer
- The basis functions $\phi_j$ can be simple functions, but they can also consist of even more basis functions, adding more and more layers to the neural network
- The weights can be determined using the binary cross-entropy loss function:
$$w^* = \arg \min_w -\sum_{i = 1}^N y_i \ln(f(x_i, w)) + (1 - y_i)\ln(1 - f(x_i, w)$$
###### Activation Functions
- An activation function is a function that is typically applied to every node of a layer, with a few exceptions such as softmax
- It translates the scores determined by the inputs and weights into more meaningful values
- An example of an activation function is the [[Linear Classification|sigmoid]] function which translates scores into probabilities
###### Singe Hidden Layer
- In a simple case, a transformation function $\phi$ may be chosen to look like this:
$$\phi(x) = (\sigma(5 + x_1 + x_2), \sigma(5 - x_1 - x_2))$$
- Combined with the logistic regression model, the resulting model would look like this:
$$f(x, w) = \sigma_1 \left ( (w_{100}, w_{110}) \cdot \sigma_2 \left (  \begin{pmatrix}
w_{000} & w_{010} & w_{020} \\
w_{001} & w_{011} & w_{021} \\
\end{pmatrix} \cdot \begin{pmatrix}
1 \\
x_1 \\
x_2 \\
\end{pmatrix} \right )\right )$$
- Here, a weight $w_{ijk}$ represents the weight in the $i$-th layer, which connects the input node $j$ to the output node $k$
###### More Hidden Layers
- In practice, mulitple hidden layers are often used, since single-layer networks may require a large number of hidden units, which leads to more parameters and slower training
- A model with a number of hidden layers may be described like so:
$$f(x, W, b) = \sigma_2(W_2 \sigma_1(W_1 \sigma_0(W_0x + b_0) + b_1) + b_2)$$
- Here $W_j$ are the weights per layer and $b_j$ the corresponding biases
- The resulting deep neural network may look like this:
![[Pasted image 20250105174949.png]]
## Beyond Binary Classification
- Neural networks can be used for a variety of prediction task
- Depending on the task, however, the activation function in the final layer, as well as the loss function for training may need to be changed
- The following table illustrates a few common choices for different supervised learning classification applications:
![[Pasted image 20250105182441.png]]
- For unsupervised learning applications, any loss function that yields a useful gradient can be used
## Parameter Learning
- In practice the loss function of a model is often not convex, meaning that it is often not possible to determine global minima
- Instead one often computes a few local minima using gradient descent and picks the one that performs best
#### Backpropagation
- Backpropagation is a popular and efficient method for the computation of a gradient of a function
###### Method 
- Backpropagation can be done via a few steps:
	1. The function $f$ is divided into a composition of smaller module functions:
	2. The derivative for every module is formulated symbolically, which means that they will not yet be evaluated for concrete inputs
	3. In the forward pass, all the module functions are evaluated at a point $x^*$ starting with the inner most module whose value is then propagated to the outer modules
	4. In the backward pass, the local derivatives, which were computed in step 2, are evaluated with the values computed in the forward pass
	5. The global derivative, i.e. the derivative of $f$, is achieved by multiplying the evaluated local derivatives
###### Computational Graph
- The module functions of a function $f$ can be arranged in a computation graph to visualize the backpropagation:
![[Pasted image 20250106160351.png]]
###### Example
- A function $f = \frac{2}{e^{-x}}$ would be split into $a(x) = -x$, $b(a) = e^a$ and $c(b) = \frac{2}{b}$
- The derivatives would be $\frac{\mathrm d a}{\mathrm d x} = -1$, $\frac{\mathrm d b}{\mathrm d a} = e^a$ and $\frac{\mathrm dc}{\mathrm db} = -\frac{2}{b^2}$
- For $x^* = 2$, the foward pass would yield $a = -2$, $b = e^{-2}$ and $c = \frac{2}{e^{-2}}$
- The backward pass yields $\frac{\mathrm d a}{\mathrm d x} = -1$, $\frac{\mathrm d b}{\mathrm d a} = e^{-2}$ and $\frac{\mathrm d c}{\mathrm d b} = -\frac{2}{e^{-4}}$
- Continuing the example, the global derivative is $f' = \frac{\mathrm d a}{\mathrm d x} \cdot \frac{\mathrm d b}{\mathrm d a} \cdot \frac{\mathrm d c}{\mathrm d b} = \frac{2e^{-2}}{e^{-4}} = \frac{2}{e^{-2}}$
###### Multiple Inputs
- If a function has multiple inputs, the derivative for each input can be computed:
$$\frac{\mathrm df}{\mathrm dx} = \frac{\mathrm dc}{\mathrm da} \cdot \frac{\mathrm da}{\mathrm dx}$$
$$\frac{\mathrm df}{\mathrm dy} = \frac{\mathrm dc}{\mathrm db} \cdot \frac{\mathrm db}{\mathrm dy}$$
![[Pasted image 20250106152241.png]]
- If it has multiple paths from the inner most module function to the result, the separate paths can be added together:
$$\frac{\mathrm df}{\mathrm dx} = \frac{\mathrm dc}{\mathrm da} \cdot \frac{\mathrm da}{\mathrm dx} + \frac{\mathrm dc}{\mathrm db} \cdot \frac{\mathrm db}{\mathrm dx}$$
![[Pasted image 20250106152423.png]]
###### Jacobian
- The principles of backpropagation can also be applied to vector fields using the field's Jacobian matrix 
- Given the vector field $f: \mathbb{R}^n \rightarrow \mathbb{R}^m$, and $a = f(x)$, the Jacobian may have the following form:
$$\frac{\mathrm d a}{\mathrm dx} = \begin{pmatrix}
\frac{\mathrm d a_1}{\mathrm dx_1} & ... &  \frac{\mathrm d a_1}{\mathrm dx_n} \\
\vdots & \ddots & \vdots \\
\frac{\mathrm d a_m}{\mathrm dx_1} & ... &  \frac{\mathrm d a_m}{\mathrm dx_n} \\
\end{pmatrix} \in \mathbb{R}^{m \times n}$$
- Now a new function $g: \mathbb{R}^m \rightarrow \mathbb{R}$ can be defined and chained together with $f$ leading to $c = g(a) = g(f(x))$
- The gradient $\nabla_a c \in \mathbb{R}^m$ is formed by transposing the derivative of $c$ with respect to $a$
$$\nabla_a c = \left( \frac{\mathrm dc}{\mathrm da} \right)^T = \begin{pmatrix}
\frac{\mathrm dc}{\mathrm da_1} & ... & \frac{\mathrm dc}{\mathrm da_m} \\
\end{pmatrix}^T$$
- Since $c$ is the result of the chaining of $g$ and $f$, it's derivative can also be formed with respect to $x$:
$$\frac{\mathrm dc}{\mathrm dx} = \frac{\mathrm dc}{\mathrm da} \cdot \frac{\mathrm da}{\mathrm dx}$$
- Here, $\frac{\mathrm dc}{\mathrm da}$ is the transposed gradient $\nabla_a c$ and $\frac{\mathrm da}{\mathrm dx}$ is the Jacobian of $f$