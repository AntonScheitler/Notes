## Discrete Modelling
- A network of service units is created, in which each offers functionality
- The flow of data packages through this network is modelled using a queuing network, in which packages wait, in order to use a service
- Stochastics are applied, since event are unpredictable when there is only partial information on the components of a system
#### Stochastical Instruments
- In a discrete modelling of data traffic, all aspects of [[Kontinuierliche Wahrscheinlichkeitsraeume|continuos probabalistics]] can be used
###### Hazard Rate
- In addition to the tools of continuous probabalistics, a hazard rate of a random variable $T$ is defined by:
$$h_T(t) = \frac{f_T(t)}{1 - F_T(t)}$$
- If, for example, $T$ is uniformly distributed, the hazard rate would be $\frac{1}{a - t}$, meaning, that if an event hasn't occured up until a point in time $t$, it is more likely to occur, as $t$ increases
- The [[Diskrete Wahrscheinlichkeitsraeume|poisson distribution]] is a distribution, with a constant hazard rate 
#### Stochastic Processes
- A model is derived from the negative exponential distribution, which yields the probability, that a time interval $t$ will separate two events:
$$f_T(t) = \upsilon \cdot e^{- \upsilon t}, \; \; \upsilon = h_T(t)$$