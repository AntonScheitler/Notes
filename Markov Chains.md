## Modelling Queuing Systems
- In a queuing system, a certain amount of jobs appears in a time frame and queues up, in order to be served by a set of service units
- The probability of a customer appearing and being served, are described by a negative exponential, or markovian, distribution
- If there is just one service unit availabe, this model can be refferd to as $M | M | 1$
#### Model Parameters
- A queuing system has multiple parameters, which influence it's behavior:
	- The arrival rate $\lambda$ describes, how many jobs appear in a time frame
	- The service rate $\mu$ describes, how many jobs are served in a time frame
	- The dwelling time $y$ is the time a job stays in the system, until it is completed
	- The filling $f$ is the number of jobs in the system
	- The throughput $d$ is the average numer of jobs completed within a time frame 
	- The maximum throughput $c$ is the maximum numer of jobs that can be completed within a time frame 
	- The utilization $r$ is the relative throughput of a system
#### Little's Law
- Little's Law puts the average filling, dwelling time and throughput into relation:
$$\mathbb{E}[f] = \mathbb{E}[d] \cdot \mathbb{E}[y]$$
#### Computing Parameters
- Normally, the arrival and service rates, as well as the number of service units in a system is known
- The other characteristics of the system need to be computed, by modelling it as a markov chain:
![[Pasted image 20240726141753.png]]
- This chain yields the following system of equations:
$$p_0 \cdot \lambda = p_1 \cdot \mu$$
$$p_1 \cdot \lambda = p_2 \cdot \mu$$
$$\vdots$$
$$p_{i - 1} \cdot \lambda = p_i \cdot \mu$$
- Which means that the following holds for $p_i$:
$$p_i = \left ( \frac{\lambda}{\mu} \right )^i \cdot p_0$$
- Using the property $\sum_{i = 0} p_i = 1$, all other parameters can be derived
###### Filling
- The average filling of a system can be described by:
$$\mathbb{E}[f] = \sum_{i = 0} i \cdot p_i$$
###### Throughput
- The average throughput $d$ can be calculated like so:
$$\mathbb{E}[d] = (1 - p_0) \cdot \mu$$
###### Dwelling Time
- In order to calculate the average dwelling time $y$, Little's law can be used:
$$\mathbb{E}[y] = \frac{\mathbb{E}[f]}{\mathbb{E}[d]}$$