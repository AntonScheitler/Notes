## Population Dynamics
- The modeling of population dynamics, either in isolation or in coexistence with different species, is a common application of continuous models 
#### Model of Malthus
- An isolated population $P$ with a birth rate $\gamma$ and a death rate $\delta$ is considered 
- The population of P at a given time $t$ can be described like so:
$$p(t + \Delta t) = p(t) + (\gamma - \delta) \cdot p(t) \cdot \Delta t$$
- This leads to an [[Differentialgleichungen|ordinary differential equation]] with a solution of:
$$p(t) = p_0e^{(\gamma - \delta) t}$$
- The population therefore grows exponentially
- Even though the population count is discrete, the model is continuous
#### Saturation by Verhulst
- Due to environmental factors and growth limits, exponential growth is unrealistic and population growth dampens, as the population increases
- This means, that the brith and death rates need to be adjusted:
$$\gamma(t) = \gamma_0 - \gamma_1p(t)$$
$$\delta(t) = \delta_0 + \delta_1p(t)$$