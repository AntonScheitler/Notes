## Principal Component Analysis
- Reducing the number of dimensions before training is critical for improving performance
- It is important to be able to distinguish "good" dimensions from ones that don't offer a lot of information
#### Linear Transformations
- Two dimensions of a dataset may be correlated in which case one of the two is redundant
- In order to eliminate redundant dimensions, the coordinate system of the data points can be transformed
- This approach of determining a coordinate system in which formerly correlated data points become linearly uncorrelated and eliminating the dimension with low variance is called principal component analysis
###### Example
- In the following example, a transformation is applied to a dataset, through which $x_2$ can be eliminated:
![[Pasted image 20250121162441.png]]
#### Approach
- In order for PCA to work, the data must be transformed, so that the covariance between the new dimensions is $0$
- This can be done via three steps:
	1. The data must be centered
	2. The covariance matrix of the centered data must be computed 
	3. Eigenvector Decomposition is used to transform the coordinate system
###### Data Centering 
- In order to center all data points, their mean must be subtracted from them, so that $\tilde{x}_i = x_i - \bar{x}$
- The mean can be computed like so:
$$\bar{x} = \begin{pmatrix}
\bar{x}_1 \\
\vdots \\
\bar{x}_d \\
\end{pmatrix} = \frac{1}{N} \cdot X^T \cdot 1_N$$
###### Computing the Covariance
- The variance of the $j$th dimension of the dataset $X$ can be computed like this:
$$Var(X_j) = \frac{1}{N} \sum_{i = 1}^N(x_{ij} - \bar{x}_j)^2 = \frac{1}{N}X^T_jX_j - \bar{x}_j^2$$
- The covariance between two dimensions $j_1$ and $j_2$ is determined like so:
$$Cov(X_{j_1}, X_{j_2}) = \frac1N \sum_{i = 1}^N (x_{ij_1} - \bar{x}_{ij_1})(x_{ij_2} - \bar{x}_{ij_2}) = \frac1N X^T_{j_1} X_{j_2} - \bar{x}_{j_1}\bar{x}_{j_2}$$
- From this the symmetric covariance matrix can be constructed:
$$\Sigma_X = \begin{pmatrix}
Var(X_1) & Cov(X_1, X_2) & ... & Cov(X_1, X_d) \\
Cov(X_2, X_1) & Var(X_2) & ... & Cov(X_2, X_d) \\
\vdots & & \ddots & \vdots \\
Cov(X_d, X_1) & Cov(X_d, X_2) & ... & Var(X_d) \\
\end{pmatrix} = \frac1N X^TX - XX^T = \frac1N \overline{X}^T\overline{X}$$
###### Eigenvector Decomposition
- Since the goal of a PCA is to set the covariances to $0$, the targeted covariance matrix has this form:
$$\Lambda = \begin{pmatrix}
Var(1) & 0 & ... & 0 \\
0 & Var(2) & ... & 0 \\
\vdots & & \ddots & \vdots \\
0 & 0 & ... & Var(d)
\end{pmatrix}$$
- To transform $\Sigma_X$ to this matrix, its Eigendecomposition needs to be determined: 
$$\Sigma_X = \Gamma \cdot \Lambda \cdot \Gamma^T$$
- The eigenvectors $\gamma_i$, which make up the columns of $\Gamma$, describe the coordinate system in which the two dimensions become uncorrelated
- The data $\tilde X$ can therefore be transformed like this:
$$Y = \tilde X \cdot \Gamma$$
- The eigenvalues $\lambda_i$ which make up the diagonal of $\Lambda$ describe the variances of the different dimensions in the new coordinate system
- Thus the dimensions with the smalles $\lambda_i$ have the lowest variance and can be dropped and only the $k$ dimensions with the largest variances remain
- The $k$ largest eigenvectors can be determined using [[Eigenwertprobleme|power iteration]]
#### Limitations
- PCA can only capture linear relationships between two dimensions
- This issue can be addressed with kernel PCAs
## Singular Value Decomposition
- Even though data points may lie in higher-dimensional space, the data itself has a lower dimensionality
- By reducing the space to the intrinsic dimensionality of the data, the number of dimensions can be reduced
#### Low-Dimensional Manifold
- Let's say the data is represented by a matrix $A$ with $n$ rows, in which each row corresponds to the coordinates of a datapoint
- If the rank of $A$ is less than $n$, it can be rewritten with fewer basis vectors, resulting in a smaller matrix $A'$
- This $A'$ captures the intrinsic dimensionality of the data
###### Low-Rank Approximation
- If the rank of $A$ is $n$, then it cannot be rewritten with different basis vectors directly
- What can be done instead is to approximate $A$ with a matrix $B$ which does have a rank lower than $n$
- In order to determine such a $B$, singular value decomposition can be used
###### Example
![[Pasted image 20250122144014.png]]
#### Latent Factors
- Decomposing a data matrix $A$ via a singular value decomposition yields $U \Sigma V^T$
- Each matrix in this decomposition carries some sort of meaning
- More specifically, $U$ and $V$ are similarity matricies that map features to some underlying meaning and $\Sigma$ measures the strength of these mappings
###### Example
- Given a matrix $A$ that represents user's movie preferences, $U$ is a similarity matrix that maps users to genere preferences, $V$ maps movies to genres and $\Sigma$ measures the strength of each genre
![[Pasted image 20250201135446.png]]
#### Reducing Dimensions
- Given a decomposition $U\Sigma V^T$ we have already determined that $\Sigma$ measures how strong the mapping to some underlying meaning is  
- If a singular value in $\Sigma$ is very small, it is therefore likely that the underlying meaning that is being mapped to is just noise or irrelevant
- By eliminating the smallest singular values, the original matrix $A$ can be approximated by a matrix with a lower rank
- The reduced data $P$ can be obtained in one of two ways:
$$P = U \Sigma$$
$$P = AV$$
###### Example
- Continuing the above example, the mapping to the sci-fi and romance genere is quite strong as indicated by $\Sigma$
- However a third genere has been picked up by the decomposition which isn't really prominent in $A$ and has a small corresponding value in $\Sigma$, which means it can be eliminated 
![[Pasted image 20250201140932.png]]
## Matrix Factorization
- In a matrix factorization, a matrix is partially populated with values
- Missing values are denoted with $0$ and must be predicted
- A regular singular value decomposition would have the form $R = QP^T$, where $Q = U\Sigma$ and $P = V$ 
- This would simply yield $0$ for all missing values instead of giving a prediction, which is why a different approach must be used
#### Latent Factor Model
- $Q$ and $P$ need to be constructed so that the following minimum is achieved: 
$$\min_{P, Q} f(P, Q) = \min_{P, Q} \sum_{(u, i) \in S} (r_{ui} - q_u \cdot p_i^T)^2$$
- Here, $r_{ui}$ denotes a non-zero entry in $R$ and $q_u, p_i^T$ are the $u$th row and $i$th column of $Q$ and $P$ respectively
- A prediction for an entry in $R$ is therefore given by:
$$\hat{r}_{ui} = q_u \cdot p_i^T$$
- There are several approaches to determine this minimum
###### Block coordinate minimization
- In a block coordinate minimization, one variable is kept fixed and the other is optimized alternatingly
- If either $q_u$ or $p_i^T$ is fixed, then $\min_{P, Q} f(P, Q)$ can be reduced to an ordinary least squares regression
###### Stochastic Gradient Descent
- A stochastic gradient descent can be performed on $f(P, Q)$ with respect to $P$ and $Q$ until it's minimum is determined
#### Regularization
- The Latent Factor Model can be regularized by adding a regularization term yielding:
$$\min_{P, Q} f(P, Q) = \min_{P, Q} \sum_{(u, i) \in S} (r_{ui} - q_u \cdot p_i^T)^2 + \lambda_1 \sum_{u} ||q_u||^2 + \lambda_2 \sum_i ||p_i||^2$$
- $\lambda_1$ and $\lambda_2$ are regularization parameters for $P$ and $Q$
- This produces a model which makes more conservative predictions is data is scarce
- Where the unregularized model could be reduced to a series of ordinary least squares regression problems, these now become ridge regression problems
#### Example
- A naive singular value decomposition would yield no useful result at all, as all predictions would be $0$:
![[Pasted image 20250201160405.png]]
## Autoencoders
- Where PCA and SVD can only capture and reduce linear data relations, Autoencoders can reduce dimensions non-linearly
- Autoencoders are neural networks which can find a latent representation $z \in \mathbb{R}^L$ of the original $x \in \mathbb{R}^D$, where $L << D$, and reconstruct $x$ from it
- The reconstruction $\hat{x}$ of $x$ therefore always lies in an $L$-dimensional subspace of $D$
#### Structure
- Autoencoders consist of an encoder, which determines the latent representation $z$ and a decoder, which reconstructs $x$ from $z$:
![[Pasted image 20250201173823.png]]