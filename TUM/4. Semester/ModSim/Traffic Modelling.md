## Hitchhikers Paradox
- Imagine a hitchhiker waiting at a highway for a car to arrive
- Cars arrive at specific intervals, each with some duration, which is described by the random variable $T$
- The hitchhiker appears sometime in the middle of one of these intervals  
#### Forward and Backward Recurrence Time
- The forward recurrence time, or FRT, is the time, the hitchhiker needs to wait for the next car to arrive
- Similarly, the backward recurrence time, or BRT, is the time that has passed since the last car passed by
- The following holds for the expectation of those times:
$$\mathbb{E}[FRT] = \mathbb{E}[BRT] = \frac{\mathbb{E}[T]}{2} \cdot (1 + \varrho(T)^2)$$
- Here, $\varrho(T)$ is the coefficient of variation $\frac{\sigma}{\mathbb{E}[T]}$ 
- The equation above has the consequence, that $\mathbb{E}[FRT] = \mathbb{E}[T]$, if $\varrho(T) = 1$
- Interestingly, it holds that $\mathbb{E}[FRT] > \mathbb{E}[T]$, if $\varrho(T) > 1$
## Traffic Flow
- When modelling the flow of traffic through a stretch of space, there are three variables to consider:
	- The speed $v$ the cars travel with
	- The density of cars $\rho$ on this stretch of space
	- The actual flow $f$ of the cars
- It holds, that $f = v \cdot \rho$
- The fundamental diagramm visualizes the relationship between speed and density
#### Constructing the Fundamental Diagram
 - The distance $\delta$ between two cars depends on the density $\rho$ and the length of a car $l$:
 $$\delta = \frac{1 - \rho \cdot l}{\rho}$$
- If there is now a relationship between $\delta$ and $v$ as well, $v$ can be described in relation to $\rho$, by substituting $\delta$ with this relationship
- An example for a relationship like this may be something like "the distance is half of the speed in meters"
- This example would lead to an expression like this:
$$v = 2000 \cdot \frac{1 - \rho \cdot l}{\rho}$$
###### Speed Restrictions
- If there is a limit on speed $v_{\max}$, this means there is a range of $\rho$, for which the speed remains unchanged
- This range lasts from $0$ to $\rho(v_{\max})$, which, in the above example, would be described like so:
$$\rho(v_{\max}) = \frac{2000}{v_{\max} + 20}$$
- Similarly, there is a range of $\rho$, for which traffic will stop completly
- This range lasts from $\rho(0)$ until infinity, where $p(0) = 100$ in this example
###### Constructing the Speed Function
- Now that the speed restrictions have been applied, a function $v(\rho)$ which calculates the speed given a density can be formulated
- Continuing the example, this function would look like this:
$$v(\rho) = \begin{cases}
v_{\max}, \text{ if } \rho \leq \rho(v_{\max}) \\
2000 \cdot \frac{1 - \rho \cdot l}{\rho}, \text{ if } \rho(v_{\max}) < \rho < \rho(0) \\
0, \text{ if } \rho \geq \rho(0) \\
\end{cases}$$
###### Constructing the Flow Function
- Using the speed function above, a function $f(\rho)$ can be created, which calculates the flow for a given density
- In this example, this function would have the following form
$$f(\rho) = \begin{cases}
v_{\max} \cdot \rho, \text{ if } \rho \leq \rho(v_{\max}) \\
2000 \cdot (1 - \rho \cdot l), \text{ if } \rho(v_{\max}) < \rho < \rho(0) \\
0, \text{ if } \rho \geq \rho(0) \\
\end{cases}$$
###### Visualization
- The flow function can be used to draw the actual fundamental diagram, which in our example looks like this:
![[Pasted image 20240726182819.png]]
#### Signal Velocity
- The signal velocity of a traffic flow model is defined as the first derivative of a flow function $f(\rho)$