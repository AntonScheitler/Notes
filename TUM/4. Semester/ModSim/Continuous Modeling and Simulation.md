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
- This results in the following differential equation:
$$\dot{p}(t) = \gamma(t) - \delta(t) = \gamma_0 - \delta_0 - (\gamma_1 + \delta_1) \cdot p(t)$$
- Which yields the solution:
$$p(t) = \frac{\gamma_0 - \delta_0}{\gamma_1 + \delta_1} + \left(p_0 - \frac{\gamma_0 - \delta_0}{\gamma_1 + \delta_1} \right) \cdot e^{-m \cdot t}$$
###### Logistic Growth
- In the saturation by Verhulst, the birth and death rate decline with the start of the population growth, which is unrealisitc, since growths usually follow an S-curved, logistic growth
- In a more refined model, an inflection point is defined, past which the population growth begins to shrink
#### Multiple Species
- If multiple species $p$ and $q$ are present, their population growths are influenced by each other and can, in general, be described like so:
$$\dot{p}(t) = f(p(t), q(t)) \cdot p(t)$$
$$\dot{q}(t) = g(p(t), q(t)) \cdot q(t)$$
- The impact of the size of $p$ and $q$ on the growth rates $f$ and $g$ can be described as $f_p, f_q$ and $g_p, g_q$, which are the derivatives of $f$ and $g$ with respect to $p$ and $q$
###### Equilibrium
- If there are population sizes $\overline{p}$, $\overline{q}$, for which the growth rates $f$ and $g$ are zero, an equilibrium is reached
- An equilibrium can be calculated, by constructing a linear set of equations from $f = 0$ and $g = 0$
- If the linear set of equations has no solutions, then an equilibrium does not exist
###### Attractiveness
- An equilibrium may or may not be attractive, meaning that it will be reached at some point
- In order to determine, whether an equilibrium is attractive, a matrix can be constructed using $f$ and $g$:
$$F(p, q) = \begin{pmatrix}
f(p, q) \cdot p \\
g(p, q) \cdot q \\
\end{pmatrix}$$
- If the real parts of the eigenvalues of the Jacobian of $F(\overline{p}, \overline{q})$ are negative, then the equilibrium $\overline{p}$, $\overline{q}$ is attractive
###### Competition
- The impact of the species on their growth rates can be described with:
$$f_p, f_q, g_p, g_q < 0$$
- This means, that the larger any population is, the slower the growth rates for all populations will be
- This is because every species is competing with itself, as well as it's competitor
- In this scenario, the existence of an equilibrium depends on if the species interferes more with itself, than it does with the other one
- If the interference from both sides is equal, an equilibrium may only be reached, if one of the species goes extinct, or it may be reached in every state
###### Predator-Prey
- If $p$ is the predator and $q$ the prey, the growth rates can be described with:
$$f_p, g_p, g_q < 0, \; \; f_q > 0$$
- This is because all species are competing with themselves and $p$ preys on $q$, however, the more prey $q$ there is, the more $p$ can grow
- The eigenvalues of the Jacobian of the equilibrium is entirely imaginary
- This means, that there is a neighborhood of stability around the equilibrium
## Control Engineering
- The controls of a technical process need to be optimized, in order to achieve a certain state
- There are different approaches to constructing these controls
#### Feedback Control
- In feedback control, the target is constantly monitored and a reference value is provided, which serves as a guideline for the controls
- The ultimate goal is to minimize the difference between the reference values and the actual measured values, produced by the controller
###### P Controller
- A P Controller contains just one variable, which is proportional to the deviation of the actual measured value from the target reference value
- Just looking at this one variable, however, may result in a permanent deviation from the reference value
###### PID Controller
- A PID Controller consists of three parts:
	- A proportional variable, which behaves just as in the P Controller
	- An integral variable, which is proportional to the cumulated deviations from the reference value and serves to counteract deviations in the long run
	- A differential variable, which is proportional to changes in the deviation from the reference value and serves to counteract oscillations
###### Example
![[Pasted image 20240531093428.png]]
#### Fuzzy Control System
- When controlling via fuzzy logic, a crisp set of values $X$ is required
- A fuzzy set $\tilde{A}$ is defined on top of $X$ like so:
$$\tilde{A} = \left \{ (x, \mu(x, X, \tilde{A}), x \in X\right \}$$
- $\mu(x, X, \tilde{A}) \rightarrow [0, 1]$ is a function, which rates how closely an element $x$ is related to the fuzzy set $\tilde{A}$
###### Operations
- Operations, such as the intersection, union, or complement of fuzzy sets are defined like so:
$$\tilde{A} \cap \tilde{B} = \left \{ \left(x, \text{min} \left \{ \mu(x, X, \tilde{A}), \mu(x, X, \tilde{B})\right \} \right ), x \in X \right \}$$
$$\tilde{A} \cup \tilde{B} = \left \{ \left(x, \text{max} \left \{ \mu(x, X, \tilde{A}), \mu(x, X, \tilde{B})\right \} \right ), x \in X \right \}$$
$$\bar{\tilde{A}} = \left \{ \left(x, \left ( 1 - \mu(x, X, \tilde{A}) \right ) \right ), x \in X \right \}$$
###### Fuzzification
- The first step in a fuzzy control system is to describe the measured values with fuzzy sets
- Here linguistic variables can be used, which describe and group crisp values, like temperatures, using linguistic terms, like "cold" or "lukewarm"
![[Pasted image 20240611094423.png]]
###### Rule Base
- The behavior of the system is defined with if-then statements which use fuzzy sets
- The if part can include a number of fuzzy sets, which are combined using intersections, unions and complements
###### Inference
- The degree of membership of the measured value in the if part of a rule determines the degree of the response in the then part of a rule
- This degree is described by a cut fuzzy set
![[Pasted image 20240611101639.png]]
###### Defuzzification
- In the defuzzification step, the cut fuzzy sets from the inference step are translated into crisp values
![[Pasted image 20240611102730.png]]
## Heat Transfer
- The propagation and distribution of heat in a physical space over time can be modeled using differential equations
- In order to describe changes in temperature across time and space, a PDE is needed
- To make this PDE unique some initial, or boundary conditions are needed 
#### Boundaries
- In a Dirichlet condition, the temperature on the boundary of the domain is given 
- In a Neumann condition, the normal derivative and therefore the heat flow through the boundary is given
- These conditions can also be combined with one another
#### Heat Equation
- The equation, which describes transfer of heat is:
$$\kappa \cdot \Delta T = T_t$$
$$\Delta T = T_{xx} + T_{yy} + T_{zz}$$
- Here, $T_s$ refers to the derivative of $T$ with respect to a variable $s$
###### Types of PDEs
- The heat equation is a linear PDE of second order, because the equation consists of a linear combinations of the function itself, its first and its second derivative
###### Classification
- The following holds for the heat equation:
$$\kappa \cdot T_{xx} + \kappa \cdot T_{yy} + \kappa \cdot T_{zz} - T_t = 0$$
- The coefficients of the second derivatives $T_{ss}$ can therefore be written as a matrix, those of the first derivative as a vector:
$$A = \begin{pmatrix}
\kappa & 0 & 0 & 0 \\
0 & \kappa & 0 & 0 \\
0 & 0 & \kappa & 0 \\
0 & 0 & 0 & 0 \\
\end{pmatrix}, \; b = \begin{pmatrix}
0 \\
0 \\
0 \\
-1 \\
\end{pmatrix}$$
- Since one of the eigenvalues of $A$ is $0$ and the others have the same sign, this is a parabolic PDE
- Classifying PDEs is important, since each class requires a different numerical approach
#### Finite Differences Method
- The finite differences method is used to approximate all occuring derivatives in a differential equation
###### Approach
- A domain is made discrete by defining a set of points on a mesh
- Each section of the mesh has a number of widths $h = (h_x, h_y, h_z)$
- The first derivatives of a differential equations can be approximated using difference quotients:
$$\frac{\delta u}{\delta x}(\xi) = \frac{u(\xi + h_x) - u(\xi)}{h_x}$$
- The second derivatives can be approximated using a 3-point-stencil:
$$\frac{\delta^2u}{\delta^2x^2} = \frac{u(\xi + h_x) - 2u(\xi) + u(\xi - h-x)}{h_x^2}$$
- Since the boundary of the mesh is given by the initial and boundary conditions of a problem, the mesh points can be calculated one by one
