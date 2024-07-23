## Approximating ODEs
- In order to find a numerical approximation for ordinary differential equations, an initial value is selected
- All subsequent values are found step by step by calculating the derivative of a given value and using it to determine the next
- There are different approaches to determine the result in each step
#### Euler's Method
- Euler's method determines the result in each step by simply using the derivative of the current value:
$$y_{k + 1} = y_k + \delta t \cdot f(t_k, y_k)$$
- Here, $y_k$ is the value of the current step and $f(t_k, y_k)$ computes the derivative of $y$ at time $t_k$
#### Method of Heun
- The method of Heun uses both the derivative of the current value, as well as the derivative of the result from a step in Euler's method
- Those two derivatives are averaged to produce the next value in each step:
$$y_{k + 1} = y_k + \frac{\delta t}{2} \big (f(t_k, y_k) + f(t_{k+1}, y_k + \delta t \cdot f(t_k, y_k)) \big )$$
#### Implicit Euler's Method
- The implicit Euler's method operates similar to the explicit one, except it uses the derivative of the result of a step for the step itself:
$$y_{k + 1} = y_k + \delta t \cdot f(t_{k + 1}, y_{k + 1})$$
#### Explicit Formulae
- An explicit formula for the result of the $k^\mathrm{th}$ step of a method can be created by setting up a recurrence relation and inserting the initial value of the problem
###### Example
- Given an initial value problem, that is defined like so: 
$$\dot{y}(t) = \lambda y(t), \; \; y(0) = 1$$
- An explicit formula for Euler's method can be computed like so: 
$$y_{k + 1} = y_k + \delta t \cdot \lambda y_k = y_k (1 + \delta \lambda)$$
$$\Rightarrow y_k = (1 + \delta \lambda)^k$$
#### Rating of Methods
- Methods can be ranked based on a few characteristics
###### Stability
- A method is considered stable, if it yields $y_k \to \infty$ as $k \to \infty$ for the following initial value problem:
$$\dot{y}(t) = \lambda y(t), \; \; y(0) = 1, \; \; \lambda < 0$$
###### Consistence
- The local discretization error is the maximum error that can occur in a single step of a method
- If the local discretization error tends towards $0$, as the time step size tends towards $0$, the method is considered consistent
###### Convergence
- The global discretization error is the maximum error that can occur over all steps of a method
- If the global discretization error tends towards $0$, as the time step size tends towards $0$, the method is considered convergent