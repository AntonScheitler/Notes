## Measures
- To be able to analyze numerical data it must be measured
- In general, a measure of center and a measure of distribution are needed in order to be able to grasp the behavior of a distribution
#### Measures of Center
- Popular measures of center are the median and the mean
- The median describes the point at the center of the dataset which splits it in half, or the average of the two center points, if there is an even number of datpoints
- The mean is the average value from all of the datapoints
#### Measures of Variability
- Popular measures of variability are the variance and standard deviation
- The empirical variance is described like so:
$$s^2_{x, n} = \frac{\sum_{i = 1}^n (x_i - \overline{x}_n)^2}{n - 1}$$
- The empirical standard deviation $s_{x, n}$ is then simply the square root of $s^2_{x, n}$
###### Percentiles
- The $k$th percentile is the value in the dataset, below which $k\%$  and above which $100\% - k\%$ of the data resides
- The median is therefore the $50$th percentile
- The interquartile range is the difference between the $75$th and $25$th percentile and can also be used as a measure of variability in the dataset, as it describes the range taken up by the "center" of the dataset
#### Measures of Correlation
- In order to compute how much two variables correlate with each other, the empirical correlation coefficient can be computed:  
$$r_{(x, y), n} = \frac{\sum_{i = 1}^n (x_i - \overline{x}_n)(y_i - \overline{y}_n)}{(n - 1)\cdot s_{x, n} \cdot s_{y, n}}$$
#### Robust Statistics
- In general, if the dataset is skewed towards a certain direction, using the median and interquartile range makes the analysis less affected by outliers
## Visualization
- In general, when comparing two numerical attributes, something like a scatterplot is most useful
- When comparing two categorical attributes, a table or heatmap is best suited
- For a combination of categorical and numerical attributes, boxplots can be used