## Hypothesis Testing
- In order to make draw conclusions from data, hypotheses need to be made
#### Procedure
- In general, we make a null hypothesis $H_0$, which states that there is nothing to be gained from the data and any observed correlation is coincidence
- Under the assumption that $H_0$ is true we then compute some summary statistic $T(X)$ of our data and check how likely it is that it can even occur
- If there's enough evidence that the observed $T(X)$ is not a coincidence, we can reject $H_0$, otherwise, we assume $H_0$ holds
## Normal Distribution
- The [[Kontinuierliche Wahrscheinlichkeitsraeume|Normal Distribution]] is very commonly used for statistical analysis
#### Quantiles
- An observation $x$ is considered the $q$-quantile of a distribution function $F$, if the following holds:
$$F(x) = Pr[X \leq x] = q$$
- Which $q$-quantile an observation is can be obtained using the $\texttt{pnorm}$ function
- Which observation a given $q$-quantile corresponds to can be obtained using the $\texttt{qnorm}$ function
#### The 68-95-99.7 Rule
- If a given dataset follows a normal distribution, about $68$% of the data falls within one standard deviation , $95$% within two standard deviations and $99.7$% within three standard deviations from the mean
#### Normal Probability Plots
- A normal probability plot has the number of standard deviations from the mean on the x-axis and the corresponding sample values on the y-axis
- Samples from the dataset are then drawn on this plot
- If the position of the samples on the plot represents a linear relationship, the data follows a normal distribution
###### Examples
![[Pasted image 20250601152707.png]]
![[Pasted image 20250601152811.png]]