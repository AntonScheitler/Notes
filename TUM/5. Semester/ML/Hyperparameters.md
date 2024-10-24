## Tuning Hyperparameters
- The goal of tuning hyperparameters is to develop the model, that performs best on unseen data
#### Approach
- To tune hyperparameters, a dataset is split into a training set, a validation set and a test set
- Using the training set and validation set, the optimal hyperparameters can be determined
- These hyperparameters can then be tested against the test set
###### Example
![[Pasted image 20241015122517.png]]
#### Overfitting
- Overfitting occurs, when the model is trained too closely on the training data
- In training, the model therefore shows very good results, but since it is generalized poorly, it underperforms on unseen data
###### Batteling Overfitting
- The model is optimized using the validation data in a training loop
- At the end of training, the model is tested against the test data set
- This test data set must only be used once, to avoid meta optimization on the test data
###### Example
![[Pasted image 20241021144659.png]]
#### K-fold Cross-Validation
- In order to optimize training, when the underlying dataset is small, the dataset is split into $K$ sections, where $K - 1$ sections are used for training and one for validation
- A different section is used for training on every training round
- Over mutliple rounds, each section will have been used once for validation and the optimal hyperparameters can be obtained by averaging the best parameters for each round
###### Leave-one-out cross-validation
- In leave-one-out cross-validation, there are as many sections, as there vectors
- This means that the validation data consists of just a single data vector
- This approach yields the optimal model but is very expensive so it should only be used on small datasets
###### Example
![[Pasted image 20241021150209.png]]