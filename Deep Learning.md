## Neural Networks
- A [[Linear Classification|logistic regression]] problem can be represented by a graph in which nodes are inputs and edges are weights that are applied to them
- Many classification problems, however, cannot be solved with just one layer of inputs and weights
- By placing multiple layers of inputs and weights after one another, a neural network can be created
- Every layer that is neither the input nor the output layer, i.e the first or last layer, is considered a hidden layer
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
#### Gradient Computation
- The gradient of a loss function can be computed in a number of ways, such as numerically or via symbolic differentiation which automates analytical computation of gradients
- A popular choice for gradient computation is backpropagation
###### Backpropagation