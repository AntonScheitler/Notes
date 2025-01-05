## Classification Problem
- In a classification, one is given a collection of observations $X = \{\mathbf x_1, \mathbf x_2, ..., \mathbf x_N\}$ and their labels $y = \{y_1, y_2, ..., y_N\}$ with $y_i \in \{1, ..., C\}$
- A classification function needs to be determined, which maps an observation to a label:
$$y_i = f(\mathbf x_i), \; i \in \{1, ..., N\}$$
#### Zero One Loss
- Zero One Loss can be used to determine the quality of a classification prediction $\hat{y}$
- In particular, zero one loss denotes the number of incorrect classifications:
$$l_{01}(y, \hat{y}) = \sum_{i = 1}^N \mathbb{I}(\hat{y}_i \neq y_i)$$
## Hyperplanes
- Hyperplanes can be used to partition a space and categorize observations inside it
- A hyperplane is defined by it's normal vector $w$ and it's distance from the origin, $w_0$
- A point $x$ in space can then be classified like so:
$$\mathbf w^T \mathbf x + w_0 \begin{cases}
= 0, \; \text{if x is on the plane} \\
> 0, \; \text{if x is on the normal's side} \\
< 0, \; \text{else} \\
\end{cases}$$
- Therefore the classification function can be defined like this:
$$\hat{y} = f(\mathbf w^T \mathbf x + w_0)$$
$$f(t) \begin{cases}
1, \; \text{if t > 0} \\
0 , \; \text{otherwise} \\
\end{cases}$$
- Given a set of lables $C = \{0, 1\}$, a data set $D = \{(\mathbf x_i, y_i)\}$ is linearly separable if there is a hyperplane, for which all features of class $0$ are on one and those of class $1$ are on the other side
#### Computing Parameters
- $w$ and $w_0$ get initialized with $0$ and are adjusted in an iterative process 
- For each misclassified sample $\mathbf x_i$, $\mathbf w$ and $w_0$ are updated like so:
$$\mathbf w \leftarrow \mathbf w \begin{cases}
\mathbf w + x_i, \; \text{if } y_i = 1 \\
\mathbf w - x_i, \; \text{if } y_i = 0 \\
\end{cases}$$ $$w_0 \leftarrow \begin{cases} w_0 + 1, \; \text{if } y_i = 1 \\ w_0 - 1, \; \text{if } y_i = 0 \\
\end{cases}$$
#### One vs Rest Classifiers
- In a one vs rest classifier a hyperplane $\mathcal{H}_i$ separates samples which are in a class $\mathcal{C}_i$ from those who are not in $\mathcal{C}_i$
- This however can lead to regions where samples are in neither of the classes
###### Example
![[Pasted image 20241115150726.png]]
#### One vs One Classifiers
- In a one vs one classifier, a hyperplane $\mathcal{H}_{ij}$ separates samples from a class $\mathcal{C}_i$ from those of a class $\mathcal{C}_j$
- This however means that there needs to be a hyperplane for every pair of classes which can lead to an explosively large number of hyperplanes
###### Example
![[Pasted image 20241115153017.png]]
#### Multiclass discriminant
- Using a multiclass discriminant, a hyperplane is created for ever class $\mathcal{C}$
- Such a hyperplane is defined by $f_c(\mathbf x) = \mathbf w_c^T \mathbf x + w_{0c}$
- A sample $\mathbf x$ is then assigned to the class, which yields the highest value for $f_c(\mathbf x)$, i. e. the class it "most belongs to"
###### Example
![[Pasted image 20241115160904.png]]
#### Limitations
- A hard decision based classifier can result in poor generalization and is hard to optimize
- Due to this fact, probabalistic models are a popular alternative
## Probabalistic Models
- Classification can be done by modelling the distribution of the class label $y$ given the sample $x$:
$$p(y = c \mid \mathbf x) = \frac{p(\mathbf x \mid y = c) \cdot p(y = c)}{p(\mathbf x)}$$
- This is called a linear discriminant analysis 
- In general, there is a generative and a discriminative approach to achieve this
#### Generative Model
- The generative model is based on Bayes' theorem and uses the following fact:
$$p(y = c \mid \mathbf x) \propto p(\mathbf x \mid y = c) \cdot p(y = c)$$
- Here, $p(y = c)$ is the prior and describes the probability of a point belonging to a class $c$ 
- $p(\mathbf x \mid y = c)$ is the class conditional and describes that a feature $\mathbf x$ is generated given that it belongs to class $c$
###### Approach
- A parametric model is chosen for the prior $p(y = c, \theta)$ and the class conditional $p(\mathbf x \mid y = c, \psi)$
- In a learning process, those parameters $\theta, \psi$ are estimated using maximum likelihood estimation which yields $\hat{\theta}, \hat{\psi}$
- Using inference, a new $x$ can be classified like so:
$$p(y = c \mid \mathbf x, \hat{\psi}, \hat{\theta}) \propto p(\mathbf x \mid y = c, \hat{\psi}) \cdot p(y = c \mid \hat{\theta})$$
- This approach can also be used to generate new data, which is why it's considered generative
###### Choose Prior Distribution
- The Categorical distribution can be used for the prior
- The parameter $\theta \in \mathbb{R}^{C}$  in this case is the probability of each class
- The following holds for the probability of a label $y$:
$$p(y = c) = \theta_c$$
- The maximum likelihood estimate is:
$$\theta_c^{MLE} = \frac{1}{N} \sum_{i = 1}^N \mathbb{I}(y_i = c)$$
###### Choose Class Conditional Distribution
- We use a multivariate normal distribution to model the probability of a feature $\mathbf x$ being generated, given that it belongs to a class $c$:
$$p(\mathbf x \mid y = c) = \mathcal{N}(\mathbf x \mid \mathbf{\mu}_c, \Sigma)$$
###### Behavior of the Posterior
- Given $\mathcal{C} = 2$, using Bayes' theorem yields:
$$p(y = 1 \mid \mathbf x) = \frac{p(\mathbf x \mid y = 1) \cdot p(y = 1)}{p(\mathbf x \mid y = 1) \cdot p(y = 1) + p(\mathbf x \mid y = 0) \cdot p(y = 0)}$$
- Simplifying results in this:
$$\Rightarrow p(y = 1 \mid \mathbf x) = \frac{1}{1 + \exp(- \mathbf w^T \mathbf x + w_0)} = \sigma(\mathbf w^T \mathbf x + w_0)$$
- This is equivalent to:
$$y \mid \mathbf x \sim \text{Bernoulli}(\sigma(\mathbf w^T \mathbf x + w_0))$$
- This can be visualized like so:
![[Pasted image 20241115170950.png]]
- The lefthand graph is the class conditional distribution and the righthand one is the resulting posterior
###### For $C > 2$
- If the number of classes is greater than two, the following holds for the posterior:
$$p(y = c \mid \mathbf x) = \frac{p(\mathbf x \mid y = c) \cdot p(y = c)}{\sum_{c' = 1}^C p(\mathbf x \mid y = c') \cdot p(y = c')} = \frac{\exp(\mathbf w_c^T \mathbf x + w_{c0})}{\sum_{c' = 1}^C\exp(\mathbf w_{c'}^T \mathbf x + w_{c'0})}$$
###### Naive Bayes
- The class conditional distribution can also be formed using the naive Bayes
- Here, it is assumed, that all features are conditionally independent, which results in this:
$$p(x_1,x_2, ..., x_d \mid y = c) = \prod_{i = 1}^d p(x_i \mid y = c)$$
- When forming the posterior, once can observe that the decision boundaries are now quadratic, as opposed to linear
![[Pasted image 20241117171042.png]]
#### Discriminative Model
- The discriminative model does not use Bayes' theorem and does not choose a prior and class conditional distribution to compute the posterior with
- Rather, the posterior is determined directly
###### Logistic Regression
- The posterior distribution is modelled to have the following form
$$y \mid \mathbf x \sim \text{Bernoulli}(\sigma(\mathbf w^T \mathbf x))$$
- Here, $\sigma = \frac{1}{1 + e^{-a}}$ is the sigmoid function, which translates the output of the model into probabilities
- The parameter $\mathbf w$ needs to chosen so that they maximize the likelihood function
- Assuming all samples are independent, the likelihood function looks like this:
$$p(\mathbf y \mid \mathbf w, \mathbf X) = \prod_{i = 1}^N p(y_i \mid \mathbf x_i, \mathbf w) = \prod_{i = 1}^N \sigma(\mathbf w^T \mathbf x_i)^{y_i} (1 - \sigma(\mathbf w^T \mathbf x_i))^{1 - y_i}$$
- With this, the following binary cross entropy loss function can be formulated:
$$E(\mathbf w) = -\ln(p(\mathbf y \mid \mathbf w, \mathbf X)) = - \sum_{i = 1}^N y_i \cdot \ln(\sigma(\mathbf w^T \mathbf x_i)) + (1 - y_i) \cdot \ln(1 - \sigma(\mathbf w^T \mathbf x_i))$$
- $\mathbf w$ needs to be chosen, so that it minimizes $E(\mathbf w)$
- Finding such a $\mathbf w$ is not possible analytically and needs to be done numerically