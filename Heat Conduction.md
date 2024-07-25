## Heat Equation
- The partial differential equation which describes the diffusion of heat through a one-dimensional object is:
$$\frac{\partial u}{\partial t} = \frac{\partial^2 u}{\partial x^2}$$
- Here, $u(t, x)$ is a function, which returns the temperature of a position $x$ at a time $t$
- Solving this equation analytically, however is not possible most of the time 
- Instead, one has to resort to discretization and approximation to determine a solution
#### Discretization
- Since the heat equation has both a temporal and spatial domain, both need to be discretized
- This means, that the spatial domain $[0, 1]$ is split into intervals, with a spacing of $h$, and the temporal domain is split into intervals, with a spacing of $\delta t$
- Therefore, where $x$ and $t$ were continuous before, they have now been simplified to something like dotted lines
#### Approximation
- Now that both domains have been discretized, their derivatives can be approximated, using difference equations
###### Spatial Derivative
- The second spatial partial derivative of $u$ can be approximated like so:
$$\frac{\partial^2 x}{\partial x} \approx \frac{u_{i - 1}^n - 2u_i^n + u_{i + 1}^n}{h^2}$$
- Here $u_i^n$ refers to the temperature of one of the dots, which has been achieved through the discretization of the model, where $n$ refers to their time and $i$ to their position
- Since the time isn't considered here and stays the same, we are essentially looking at series of dots in space
- If these dots are then written as a vector $u^n = (u_0^n, u_1^n, ..., u_m^n)^T$, the approximation can be reformulated to use a matrix-vector multiplication:
$$A = \begin{pmatrix}
-2 & 1 &   &   &   & \\
1 & -2 & 1 &   &   & \\
  & 1 & -2 & -1 &  & \\
  & & \ddots & \ddots & \ddots & \\
 &  &  & 1 & -2 & 1\\
\end{pmatrix} \cdot \frac{1}{h^2}$$
$$\frac{\partial^2 x}{\partial x} \approx A u^n$$
###### Temporal Derivative
- The first temporal partial derivative of $u$ is approximated like so:
$$\frac{\partial u}{\partial t} \approx \frac{u_i^{n + 1}- u_i^{n}}{\delta t}$$
- Instead of just looking at single point in space $i$, for two timesteps $n$ and $n+1$, the entire vectors of spacial points $u^n$ and $u^{n + 1}$ at those timesteps can be considered:
$$\frac{\partial u}{\partial t} \approx \frac{u^{n + 1}- u^{n}}{\delta t}$$
#### Solving the Heat Equation
- With the spacial and temporal derivatives approximated, they can be substituted into the heat equation:
$$\frac{u^{n + 1}- u^{n}}{\delta t} = A u^n$$
- Solving for $u^{n + 1}$ yields:
$$u^{n + 1} = u^n + \delta t \cdot A u^n$$
$$u^{n + 1} = (I + \delta t \cdot A) \cdot u^n$$
###### Initial Values
- For this approach to work, inital values for $u(t, 0)$ and $u(t, 1)$, as well as $u(0, x)$ need to be provided
- Often, $u$ is chosen, so that $u(t, 0) = u(t, 1) = 0$ and $u(0, x) = u_0(x)$, where $u_0: [0, 1] \to \mathbb{R}$
###### Convergence
- For the above solution to converge to $0$, as $t \to \infty$, the following needs to hold for the timestep $\delta t$:
$$\delta t < \frac{1}{\lambda_{\max}}$$
- Here $\lambda_{\max}$ refers to the largest eigenvalue of the matrix $A$
