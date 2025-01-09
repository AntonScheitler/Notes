## Structured Data
- A neural network can use different types of layers for specific tasks
- These layers leverage the known structure of the data related to their task
#### Convolutional Neural Networks
- Processing images with regular feed-forward neural networks leads to an explosion in the number of parameters
- Instead, convolutional neural networks, or CNNs, can be used, which exploit the high local correlation that pixels in an image tend to have
- CNNs use cross-correlation, in which they consider an $L \times M$ subsection of an image and score it, based on how well it matches the desired pattern:
$$\hat{x}(i, j) = \sum_{l = 1}^L\sum_{m = 1}^M x(i + l, j + m) \cdot k(l, m)$$
- Here $x(i + l, j +m)$ is a specific pixel and $k(l, m)$ the weight or kernel that applies the score
- The $L \times M$ subsection moves across the input image using a sliding window mechanism with a stride that can be increased to downsample the input and decrease the size of the output
###### Padding
- In order to regulate the size of the output of a CNN layer, padding can be applied to the input
- VALID padding applies no padding at all, making the output smaller than the input, SAME padding preserves the size of the input and FULL padding increases the size of the output
![[Pasted image 20250107114458.png]]
###### Pooling
- With pooling, subsections of convolved features can be aggregated in a sliding window mechanism, which reduces the impact of small changes within a subsection
- Different variants of pooling use different aggregation functions, such as max, mean and so on
![[Pasted image 20250107134616.png]]
###### Example
![[Pasted image 20250107112441.png]]
## Training Deep Neural Networks
- A deep neural network is trained by tuning its weights so that the loss on the training data is minimized
- In this regard, the initialization of weights is crucial for successful training
#### Naive Weight initialization
- The two problems that can occur in a naive weight initialization are weight symmetry and weight scale
###### Weight Symmetry
- Weight symmetry occurs when two hidden units have the same bias and the same incoming and outgoing weights
- This means that those units will always have gradient and cannot be trained to extract different features
- This can be solved by assigning small, random values to all weights 
###### Weight Scale
- If a hidden unit has a large number of incoming or outgoing weights that follow a distribution with a mean of $0$ and variance of $1$ , the resulting gradients vanish or explode
- This is because if the weights are too close to $0$, the gradients become very small and if the weights get too large, the gradients become very large
- That can be avoided by decreasubg variance of the weights
#### Xavier Glorot Initialization
- In a Xavier Glorot initialization, the weight matricies follow a distribution with a mean of zero and a variance of $Var(W) = \frac{2}{\text{fan-in} + \text{fan-out}}$, which avoid weight scaling problems
#### Regularization
- In order to avoid overfitting, a neural network must be regularized
- Regularization can be accomplished by applying an $L2$ norm penalty and combining it with early stopping, the injection of noise or dropout
###### Dropout
- Dropout is a regularization technique in which the values of hidden units are randomly set to $0$
- This works because it stops units from relying on any one input feature, as it may be set to $0$ randomly
#### Batch Normalization
- Normalizing the activation function outputs makes sure that the scale of every layer's input remains consistent, which leads to faster training
- This can be achieved via batch normalization: 
$$\hat{x} = \frac{x - \mathbb{E}_B(x)}{\sqrt{\text{Var}_B(x)} + \epsilon}$$
$$y = \gamma \hat{x} + \beta$$
- Here $\mathbb{E}_B$ and $\text{Var}_B$ represent the expectation and variance of the output of layer $B$ and $\gamma$ and $\beta$ are scale parameters and offsets which are also tuned during training