## Basic Concepts
- Given a training dataset of categorized vectors, the $k$ nearest neighbors approach yields the category for new vectors
- To determine the category of a new vector, the categories of its $k$ nearest neighbors are counted and the majority is chosen
- The [[Classification Performance|performance of the classification]] can be improved by weighing a vector's neighbors based on their distance from it
#### Distance Measuring
- A number of distance measures can be used, in order to determine the distance between two neighbors 
#### Hyperparameter $k$
- The number $k$ of the neighbors the model considers is a hyperparameter, that needs to be tuned
###### Tuning Hyperparameters
- To tune hyperparameters, the dataset is split into a training set, a validation set and a test set
- Using the training set and validation set, the optimal hyperparameters can be determined
- These hyperparameters can then be tested using the test set
![[Pasted image 20241015122517.png]]
###### Example
![[Pasted image 20241015122632.png]]
## Classification Pitfalls
- Certain classification errors can appear, if a few of the common pitfalls aren't avoided
#### Standardization
- Many models are sensitive to differences in scale
- To work around this sensitivity, the training data is standardized, so that the mean is always $0$ and variance always $1$
- Given a set of training vectors $x_i$, the training set can be standardized as follows:
$$x_{i, \text{std}} = \frac{x_i - \mu_i}{\sigma_i}$$
###### Handling Input and Output
- Once the model has been trained, and is being used, inputs will not adhere to the standardization automatically
- As such, they need to be standardized before being fed to the model and it's output needs to be destandardized accordingly
#### Dimensionality
- The more dimensions the input space has, the less of the space is covered by the same amount of vectors
- For a precise classification, the number of vectors thus needs to grow exponentially with the number of features
###### Example
![[Pasted image 20241018160305.png]]
## todo
- dimensionality