## Population Growth Models
- In general, the growth of any population is described by differential equations
- Depending on the type of model, those differential equations depend on a birth and death rate, some carrying capacity or the size of another population
- Stationary points of a model mark the moments, at which a population stops growing
#### Malthusian Model
- In a Malthusian model, the change in population size depends only on the current population, as well as some growth rate $\gamma$ and death rate $\delta$:
$$\dot{p}(t) = (\gamma - \delta) p(t)$$
- This equation has the following analytical solution:
$$p(t) = p_0 e^{(\gamma - \delta) t}$$
#### Carrying Capacity
- If the environment of a population has some carrying capacity $K$, and the population has a birth rate $\gamma$ and death rate $\delta$, the growth can be modeled like so: 
$$\dot{p}(t) = (\gamma - \delta) p^2 \left ( 1 - \frac{p}{K}\right )$$
- In this model, a stationary point is reached, once the population hits the carrying capacity 
- The derivative of $\dot{p}$ with respect to $p$, or $\frac{\mathrm{d}\dot{p}}{\mathrm{d}p}$ can be used to describe the behavior of the growth rate inbetween stationary points
#### Predator-Prey Models
- In a predator-prey model, there are two species $u$ and $v$, with co-dependent growth rates
- As such, their growth rates can be described like so:
$$\dot{u}  = u \cdot f(u, v)$$
$$\dot{v}  = v \cdot g(u, v)$$
- Since a member of a population is always competing with other members of the same population, $f_u$ and $g_v$ are always negative
- If $u$ preys on $v$, $f_v$ is positive, since a large amount of prey leads to a greater number of predators and $g_u$ is negative, since more predators lead to a smaller number of prey
###### Steady States
- A steady state is achieved, if $\dot{u} = \dot{v} = 0$
- The population numbers which lead to a steady state are referred to as $\overline{u}$ and $\overline{v}$
- In order to determine, whether the steady state is attractive or not, the following Jacobian needs to be computed:
$$J_{f,g}(u, v) = \begin{pmatrix}
u \cdot f(u, v) \\
v \cdot g(u, v) \\
\end{pmatrix}$$
- For $J_{f, g}(\overline{u}, \overline{v})$ the following holds:
	- If $J_{f, g}(\overline{u}, \overline{v})$ is negative definite, the steady state is attractive
	- If $J_{f, g}(\overline{u}, \overline{v})$ is positive definite, the steady state is repulsive
	- If $J_{f, g}(\overline{u}, \overline{v})$ is semi definite, the steady state is a saddle point