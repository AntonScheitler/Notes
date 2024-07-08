## Discrete Modelling
- A network of service units is created, in which each offers functionality
- The flow of data packages through this network is modelled using a queuing network, in which packages wait, in order to use a service
- Stochastics are applied, since event are unpredictable when there is only partial information on the components of a system
#### Stochastical Instruments
- In a discrete modelling of data traffic, all aspects of [[Kontinuierliche Wahrscheinlichkeitsraeume|continuos probabalistics]] can be used
###### Hazard Rate
- In addition to the tools of continuous probabalistics, a hazard rate of a random variable $T$ is defined by:
$$\vartheta = h_T(t) = \frac{f_T(t)}{1 - F_T(t)}$$
- If, for example, $T$ is uniformly distributed, the hazard rate would be $\frac{1}{a - t}$, meaning, that if an event hasn't occured up until a point in time $t$, it is more likely to occur, as $t$ increases
- The [[Diskrete Wahrscheinlichkeitsraeume|poisson distribution]] or its counterpart, the negative exponential distribution $f_T(t) = \vartheta \cdot e^{-\vartheta t}$ are distributions with a constant hazard rate
#### Modell Construction
- The model consists of a view parameters:
	- Service units $SU$ which offer functionality and jobs, which require that functionality
	- The dwelling time $y$, which is the time a job needs to be serviced by an $SU$ and the service time $b$, which is the dwelling time without potential waiting
	- The capacity $k$ and the current filling $f$ of a $SU$
	- The average and maximum throughput $d$ and $c$, as well as the utilization $\frac{d}{c}$ of an $SU
###### Little's Law
- Little's Law can be used to describe the average filling of a model, based on it's throughput and dwelling time:
$$\overline{f}(t_1, t_2) = d(t_1, t_2) \cdot \overline{y}(t_1, t_2)$$
#### Queuing Systems
- In a Queuing System, multiple $SU$ with their own queues are introduced 
- If an $SU$ is occupied, jobs that requrie the $SU$ have to wait in the respective queue
- Queuing Systems are classified by their distribution of the arrivals and of the service times, as well as their number of $SU$
- The distribution of the arrivals and of the service times is usually assumed to be the negative exponential distribution
###### Arrival Rate
- The arrival rate can be expressed like so:
$$h_T(t) = \mathbb{E} \left( \frac{\text{No. events in } [t_1, t_2]}{t_2 - t_1} \right )$$
#### Queuing Networks
- A queuing network is a graph of queuing systems, where the nodes represent queuing systems and the edges represent the different paths a job can take
###### Load
- Each job has a task stream, which describes, which $SU$ it will visit in what order
- The set of such streams is the load and is applied to the queuing network
###### Visits and Bottlenecks
- The number of visits of a node $i$ can be described using the throughput of $i$ and that of the network itself:
$$v_i = \frac{\mathbb{E}[d_i]}{\mathbb{E}[d_s]}$$
- A node is a bottleneck, if it has the highest utilization in the network, since an increase in vists would only lead to higher wait times
###### Asymptotic Behavior
- If the filling of the network increases slightly, the throughput of the system rises as well, as the number of visits increases for each node 
- As the filling increases asymptotically, however, the throughput of the system levels off and the dwelling time begins to increase linarly
#### Markov Processes
- In a Markov process, the probability of a new state depends only on the current state 
- A Markov process is homogeneous, if the transition probabilities are independent of time
- Those HMP can be applied to the graph of a queuing network and it's nodes, or states, can be classified based on their reachability
###### Classification
- A network is irreducible, if every state can be reached from ever other state
- A state is recurrent with a recurring time of $k$, if will be reached with a probability of $1$ within $k$ steps
- A state is null recurrent, if it will be reached with a probability of $1$, but only as $k \to \infty$
- A state is transient, if the probability of it's recurrance is $< 1$
###### Example
![[Pasted image 20240707152818.png]]