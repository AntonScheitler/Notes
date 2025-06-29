## Introduction Statistical Learning
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
- Often, the Root Mean Squared Error is preferred, as it is on the same scale as the original data and therefore easier to interpret: 
$$RMSE = \sqrt{MSE}$$
###### Bias-Variance Tradeoff
- The bias-variance tradeoff can be best explained with a polynomial regression model 
- As a model is trained, its MSE usually follows a U-shape, as the degree of the regression polynomial increases 
![[Pasted image 20250608110200.png]]
- This U-shape is due to the bias and variance of a model influencing its accuracy
- If a model is biased, it failes to fundamentally capture the true relationship between inputs and outputs because the function chosen to make this inference is too simple, or in this case the degree of the regression polynomial is too small
- If the variance fo a model is too high it captures random noise in the data too accurately and generalizes poorly because the function that makes the inference is too complex and the degree of the regression polynomial is too high
![[Pasted image 20250608111847.png]]
#### Hyperparameters
- Certain classification or regression algorithms have certain parameters that need to be adjusted for the model to perform at its best, like the degree of a regression polynomial or the number of neighbors in a kNN classification
- These parameters are referred to as hyperparameters and they need to be tuned by trying out different ones over many iterations of training
###### Training
- When training a model, the dataset is split into training and testing data where the former is used to create the model and the latter is used to compute its MSE
- The hyperparameters that lead to the lowest MSE can then be considered optimal
- Additionally, a cross-validation technique can be used in which the data is split into folds and a different fold is used as the testing set every time
![[Pasted image 20250608113103.png]]
## Linear Regression
- In a linear regression we assume that there is a linear relationship between inputs and outputs:
$$f(X) = \beta_0 + \beta_1 \cdot X + \epsilon_0$$
$$y = f(X)$$

- Here $\epsilon_0$ is some error and $\beta_0$, as well as $\beta_1$ are the optimal regression parameters that we seek to approximate with our estimated parameters $\hat{\beta}_0$ and $\hat{\beta}_1$ resulting in our approximation function $\hat{f}(X)$
#### Least Squares
- In order to determine $\hat{\beta}_0$ and $\hat{\beta}_1$, the least squares estimate is used, in which the two parameters are chosen so that they minimize the following error function:
$$\hat{\beta}_0, \hat{\beta}_1 = \arg \min_{b_0, b_1}RSS(b_0, b_1) = \sum_{i = 1}^n ((b_0 + b_1 x_i) - y_i)^2$$
- After the parameters have been determined, a prediction given a dataset $X$ can be formed like so:
$$y \approx X \hat{\beta} = \begin{pmatrix}
1 & x_1 \\
1 & x_2 \\
\vdots & \vdots \\
1 & x_n
\end{pmatrix} \cdot \begin{pmatrix}
\hat{\beta}_0 \\
\hat{\beta}_1 \\
\end{pmatrix}$$
- Also, there is a closed-form solution that yields the parameters that minimize the error function:
$$\hat{\beta} = (X^TX)^{-1}X^Ty$$
#### Measures of fit
- Different approaches can be taken in order to evaluate how well a model actually fits the actual dataset
###### Residual Plot
- One way to measure the fit of a model is a residual plot, in which the regression line is drawn on top of the datapoints
![[Pasted image 20250615124316.png]]
###### RSE
- Alternatively in order to compute a measure of the quality of the fit, the residual standard error can be used:
$$RSE = \sqrt{\frac1{n - 2}RSS}$$
- This measures the standard deviation of $\epsilon_0$ under the assumption that $y = \beta_0 + \beta_1 \cdot X + \epsilon_0$
- This residual standard error is computed, among many other measures, by the `glance` function in R and is denoted by `sigma`
###### $\text{R}^2$
- RSE measures the lack of fit in units of the response variable $Y$
- In order to obtain a measure that is independent of the scale of $Y$, the $R^2$ measure can be used, which is computed like so:
$$R^2 = 1 - \frac{\sum_{i = 1}^n (y_i - \hat{y}_i)^2}{\sum_{i = 1}^n (y_i - \overline{y}_n)^2}$$
- $R^2$ describes what percentage of the variance in the observed data can be explained by the model, which means that with $R^2 = 1$ the model would perfectly explain why the variance in the data is the way it is
## Multiple Linear Regression
- In most cases, a response variable cannot be simply predicted with just one explanatory variable
- The simple linear regression model can be expanded, to include multiple explanatory variables by giving each it's own weight $\beta_i$:
$$Y_i = \beta_0 + \beta_1 x_{i, 1} + ... + \beta_k x_{i, k} + \epsilon_i$$
$$Y = X\beta + \epsilon$$
#### Computing the Weights
- As with a simple linear regression, the weights for the linear regression involving mulitple variables can also be computed using the least squares method, except that now there are more weights:
$$\hat{\beta} = \arg \min_{b}RSS(b) = \sum_{i = 1}^n ((b_0 + b_1 x_{i, 1} + ... + b_k x_{i, k}) - y_i)^2$$
$$\hat{\beta} = (X^TX)^{-1}X^Ty$$
- Estimats can then be computed like so:
$$\hat{y} = X \hat{\beta} = X (X^TX)^{-1}X^Ty = Hy$$
- Here, $H$ is referred to as the hat matrix
#### Measures of fit
- When using mulitple variables, $R^2$ will increase as the number of explanatory variables grows, leading to a biased estimate of the percentage of variablility
- In order to account for this, an adjusted $R^2$ estimator can be computed:
$$R_{adj}^2 = 1 - \frac{\sum_{i = 1}^n (y_i - \hat{y}_i)^2}{\sum_{i = 1}^n (y_i - \overline{y}_n)^2} \cdot \frac{n - 1}{n - k - 1} = R^2 \cdot \frac{n - 1}{n - k - 1}$$
- There's also an alternative to the adjusted $R^2$ called AIC, which accomplishes the same goal:
$$\text{AIC} = \text{constant} + n \cdot \ln \left (\frac{\text{RSS}}{n} \right ) + 2(k + 1)$$
#### Multicollinarity
- Multicollinarity occurs if the explanatory variables are not independent and instead correlate among themselves
- If two variables are not independent, they are considered collinear
- If this is the case, the weights for the linear regression model can become hard to interpret
#### Subset Selection
- Because variables may be collinear, an optimal subset of all variables must be selected to form a model
- To find such a subset different approaches are possible
###### Best Subset Selection
- In the best subset selection algorithm, a regression is performed for every subset of the $k$ variables and the best performing subset is then considered the optimal one 
- This selection is not trivial, as the $R^2$ value will decrease, as the number of variables increases
###### Forward Stepwise Selection
- The best subset selection is computationally very expensive and stepwise approaches are therefore a good alternative 
- The forward stepwise selection starts with a model that has only an intercept
- In every step, the model is extended with each variable that is not part of the subset yet 
- The variable which delivers the greatest improvement to the model is considered optimal and included in the subset, until no more improvement gains are made
###### Backward Stepwise Selection
- Backward stepwise selection is very similar to foward stepwise selection, except that it starts with a model containing all $k$ variables and on each step removes the variable, whose removal delivers the greatest improvement 
###### Hybrid Methods
- Hybrid methods are a mix of forward and backward stepwise selections in which a variable can be added or removed each step
## Logistic Regression
- In a logistic regression model, a [[Linear Classification|hyperplane]] is defined using the weights $(\beta_0, \beta_1, ..., \beta_n)$ and used to divide a dataset into two categories
- New datapoints can be classified by determining on which side of the hyperplane they are on, which can be computed via $\mu_i = \beta_0 + \beta_1 x_{i, 1} + ... + \beta_n x_{i, n}$
- In order to convert $\mu_i$ into a probability that specifies if $x_i$ belongs to one class or the other, the sigmoid function, also called the inverse of the logit function, is used:
$$p(y_i = 1 \mid x_i) = \sigma(\mu_i) = \frac{1}{1 + \exp(-\mu_i)}$$
#### Odds
- Since Logistic Regression deals with binary classification, it's helpful to talk about the odds of a datapoint belonging to one class or the other
- The odds of the event $\{Y_i = 1\} \mid x$, i.e. the classification of the datapoint $x$ to class $1$, is defined like so:
$$\text{odds}(\{Y_i = 1\} \mid x) = \frac{Pr(\{Y_i = 1\} \mid x)}{1 - Pr(\{Y_i = 1\} \mid x)}$$
- Applying the sigmoid function yields:
$$\text{odds}(\{Y_i = 1\} \mid x) = \exp(\beta_0) \cdot \exp(\beta_1 x_{i, 1}) \cdot ... \cdot \exp(\beta_n x_{i, n})$$
- The log odds, or logit is also often used and defined by $\log(\text{odds}(\{Y_i = 1\} \mid x))$
- In oder to interpret a logistic regression model, one needs to know how odds of a prediction change, if one of the predictors changes, which can be done with the odds-ratio:
$$OR = \frac{\text{odds when } x_{i, j} = x_{i, j} + 1}{\text{odds when } x_{i, j} = x_{i, j}} = \frac{e^{\beta_0} \cdot e^{\beta_1 x_{i, 1}} \cdot ... \cdot e^{\beta_j (x_{i, j} + 1)} \cdot ...}{e^{\beta_0} \cdot e^{\beta_1 x_{i, 1}} \cdot ... \cdot e^{\beta_j x_{i, j}} \cdot ...} = e^{\beta_j}$$
#### Estimation
- In order to find optimal parameters $\beta_0, \beta_1, ..., \beta_n$ for a given dataset $X$ and it's classification $y$, the following likelihood function is used:
$$L(y \mid X, \beta) = \prod_{i = 1}^n \sigma(\mu_i)^{y_i} \cdot (1 - \sigma(\mu_i))^{1 - y_i}$$
- The the optimal estimate $\hat{\beta}$ for $\beta$ is then defined as:
$$\hat{\beta} = \arg \max_{\beta} L(y \mid X, \beta)$$
- In R, a logistic regression model can be created via the `glm` function by setting the `family` argument to `binomial`
#### Relative Risk
- It is important not to confuse the odds ratio with relative risk
- Just because changing a variable leads to an odds ratio of $5$, for example, that doesn't mean that the event is $5$ times as likely when changing this variable
- In order to obtain the relative risk, the `oddsratio_to_riskratio` function in R can be used
#### Measures of Accuracy
- Since logistic regression deals with classification, the measure of accuracy for such a model are the true/false positive and true/false negative rates
![[Pasted image 20250629145140.png]]
- From these rates the sensitivity and specificity can be deduced:
$$\text{sensitivity} = \frac{\# \text{TP}}{\# \text{TP} + \# \text{FN}}$$
$$\text{specificity} = \frac{\# \text{TN}}{\# \text{TN} + \# \text{FP}}$$
- Youden's J statistic summarizes information about sensitivity and specificity of a model: 
$$J = \text{sensitivity} + \text{specificity} - 1$$
- The Receiver Operating Characteristic curve, or roc curse, visuallizes the tradeoff between sensitivity and specificity for different classification thresholds:
![[Pasted image 20250629151847.png]]
- The larger the area under the curve, the higher the predictive ability of the model