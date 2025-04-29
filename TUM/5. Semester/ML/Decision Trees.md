## Binary Split
- A decision tree consists of nodes, which are conditions
- Depending on if the condition is true or false, one of the child nodes is visited
- Visually speaking, each node splits the remaining dataset in two
- The leaf of such a tree contains the distribution of samples, that the input vector is classified with
#### Model Training
- The [[Hyperparameters|hyperparameters]] for this model are the conditional nodes that are tested on every layer of the tree
- However, the number of possible values quickly explodes, as the decision tree grows deeper 
- Therefore a different approach than testing every single node, needs to be taken in order to optimize the hyperparameters
###### Missclassification Rate
- The missclassification rate describes how likely it is, that the classification of an input vector is incorrect
- The missclassification rate $i_E$ in a node $t$ can be described like so:
$$i_E(t) = 1 - \max_c p(y = c \mid t)$$
- The hyperparameters can be tuned by maximizing the improvement when performing a split
- The improvement is given by:
$$\Delta i(s, t) = i(t) - p_L \cdot i(t_L) - p_R \cdot i(t_R)$$
- Here $p_L$ is the probability that an input node will follow the left child of a node
###### The Problem with Missclassification Rate
- Due to it's linearity, the missclassification rate does a poor job in distinguising splits, that are good and ones that are bad
- In order to properly identify, which split is best, measures such as entropy or the Gini index are used 
- Entropy for a node $t$ is computed like so: 
$$i_H(t) = - \sum_{c_i \in C} \pi_{c_i} \log_2(\pi_{c_i})$$
- The Gini index for a node $t$ is described like this:
$$i_G(t) = 1 - \sum_{c_i \in C} \pi_{c_i}^2$$
- Here, $\pi_{c_i}$ describes the probability, that an input vector has the label $c_i$ in the node $t$
###### Visualization
- The following graph compares entropy, the Gini index and missclassification rate and relates their value to the pureness of the underlying data
- This shows, that entropy and the Gini index lead to splits, that increase pureness drastically
![[Pasted image 20241021111606.png]]
#### Stopping Criteria
- Aside from avoiding the regular pitfalls of [[Hyperparameters|overfitting]], certain stopping criteria can be defined, to avoid suboptimal models
- Those criteria are
	- the distribution of a branch is pure
	- the maximum depth of the tree has been reached
#### Example
![[Pasted image 20241018164717.png]]
## Ensembles
- Different approaches to training might lead to improved results
#### Bagging
- In bagging, multiple models are trained with different hyperparameters and combined into one
- When classifying, all models are considered and the input is classified based on the plurality of the output of the models
- When bagging decision trees, a random forest is created
###### Avoiding Pitfalls
- When building a random forest, not only the hyperparameters should differ, but the trees should also be trained on different datasets
- Those datasets can be obtained by splitting the original dataset
#### Boosting
- In boosting, training starts with a weak learner, which is incrementally improved
- Misclassified examples are weighted more heavily in subsequent steps, to improve learning