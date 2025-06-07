## Statistical Learning
- Statistical Learning is a method to derive predictions or estimations based on some input data
- If the output of a Statistical Learning method is numerical, it is considered a regression model 
- If it is categorical, one refers to it as a categorical model
#### Modelling Approach
- The inputs $X$ and the output $Y$ have the following relationship
$$Y = f(X) + \epsilon_0$$
- Here, $f$ describes the relationship between $X$ and $Y$ and $\epsilon_0$ describes the error that each observation has in this relationship 
###### Linear Classification
- In a linear classification, $f$ is assumed to be a linear function, so that it can be described like so:
$$f(x) = \beta_1 x + \beta_0$$
- Where $\beta_1$ and $\beta_0$ are parameters that need to be chosen optimally, so that the resulting error from $f(X) - Y$ is minimized
- This can be done using the method of least squares
###### kNN Regression
- In a kNN regression, the regression line is drawn according to the nearest neighbor of given point or prediction:
$$f(X) = \frac1k(x_1, ..., x_k)$$
#### Measuring Modeling Quality
- The quality of the chosen model can be measured in lots of different ways
- Usually the data used for modelling is split into a training and a testing group, where the training data is used to obtain the actual model and the testing data is used to verify it's correctness
###### Mean Squared Error
- The mean squared error, or MSE, is a commonly used measure of the quality of a fit and is described like so:
$$MSE = \frac1n \sum_{i = 1}^n (y_i - f(x_i))^2$$