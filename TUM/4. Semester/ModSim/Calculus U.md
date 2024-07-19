## Domains
- A point $x_0 \in \mathbb{R}^n$ is considered an inner point of a domain $D \subseteq \mathbb{R}^n$, if there is sphere centered around $x_0$, which fully lies in $D$:
$$\exists \space \varepsilon \in \mathbb{R}: B_{\varepsilon}(x_0) = \left \{ x \in \mathbb{R}^n \mid ||x - x_0|| < \varepsilon \right \} \subseteq D$$
- The set $\dot{D}$ of all inner points of $D$ is called the interior of $D$
- A point $x_0 \in \mathbb{R}^n$ is considered a boundary point of $D \subseteq \mathbb{R}^n$, if it lies directly on the surface of the sphere of $D$:
$$B_{\varepsilon}(x_0) \cap D \neq \emptyset \space \text{and} \space B_{\varepsilon}(x_0) \cap (D^C) \neq \emptyset, \space \text{where} \space D^C = \mathbb{R}^n \setminus D$$
- The set $\partial D$ of all boundary points of $D$ is called the boundary of $D$
- The set $\overline{D} = D \cup \partial D$ is called the closure of $D$
#### Types
- $D$ is open, if $D = \dot{D}$
- $D$ is closed, if $D = \overline{D}$
- $D$ is bounded, if all vectors in $D$ have a limited length
- $D$ is compact, if it is closed and bounded
## Partial Differentiation
- When dealing with multiple variables, a function needs to be partially derived with respect to individual variables
- Functions are classified as scalar fields, if they have the form $f: \mathbb{R}^n \to \mathbb{R}$ and vector fields, if they have the form $f: \mathbb{R}^n \to \mathbb{R}^m$
- The partial derivative of a function $f$ with respect to the variable $x_i$ is written as $f_{x_i}$
#### Gradient
- The gradient of a scalar field $f$ at a point $a$ is defined as:
$$\nabla f(a) = \begin{pmatrix}
f_{x_1}(a) \\
\vdots \\
f_{x_n}(a) \\
\end{pmatrix}$$
- This vector represents the steepest ascent from $a$
- As a result, the steepest ascent from $a$ is represented by $\nabla f(a)$
#### Hessian Matrix
- The hessian matrix of scalar field $f$ is defined using its second partial derivatives:
$$H_f(x) = \begin{pmatrix}
f_{x_1 x_1}(x) & ... & f_{x_1 x_n}(x) \\
\vdots & & \vdots \\
f_{x_n x_1}(x) & ... & f_{x_n x_n}(x) \\
\end{pmatrix}$$
#### Taylor Expansion
- In order to compute the Taylor Expansion of a scalar field $f$, it's gradient and hessian matrix are needed
- Using them, the Taylor Expansion of $f$ at a point $a$ can be described like so:
$$T_{f, a}(x) = f(a) + \nabla f(a)^T(x - a) + \frac{1}{2} (x - a)^T H_f(a)(x - a)$$
- Here, $a$ and $x$ are vectors representing the point of at which the Taylor Expansion is computed as well as the point, where it is evaluated
#### Jacobian Matrix
- A jacobian matrix $Df(x)$ is needed, in order to define the partial derivative of a vecor field $f$ with the form:
$$f(x) = \begin{pmatrix}
f_1(x_1, ..., x_n) \\
\vdots \\
f_m(x_1, ..., x_n) \\
\end{pmatrix}$$
- The rows of $Df(x)$ are equivalent to gradients of the component functions $f_1, ..., f_n$:
$$Df(x) = \begin{pmatrix}
\nabla f_1(x)^T \\
\vdots \\
\nabla f_m(x)^T \\
\end{pmatrix}$$
## Roots and Optima
- The procedures for finding roots and optima of scalar and vector fields are different from finding those of functions of the form $f: \mathbb{R} \to \mathbb{R}$  
#### Roots
- In order to approximate the root of function $f$, Newton's method needs to be used
- In general, Newton's method has the following form:
$$x_{k + 1} = x_k - \frac{f(x_k)}{f'(x_k)}$$
- What $f'(x)$ is, depends on the type of function at hand
###### Scalar Fields
- If the root of a scalar field needs to be determined, $f'(x)$ takes the form of the gradient $\nabla f(x)$
- This means, a step in Newton's method can be described as:
$$x_{k + 1} = x_k - \frac{f(x_k)}{\nabla f(x_k)}$$
###### Vector Fields
- If the root of a vector field needs to be determined, $f'(x)$ takes the form of the Jacobian Matrix $J_f(x)$
- This means, a step in Newton's method can be described as:
$$x_{k + 1} = x_k - J_f(x)^{-1} \cdot f(x_k)$$
#### Optima
- In order to find all extrema of a scalar field $f: D \subseteq \mathbb{R}^n \rightarrow \mathbb{R}$, the root of its gradient needs to be determined
- All points $x_i$ with $\nabla f(x_i) = 0$ are called critical points of $f$
###### Types of extrema
- For a critical point $x_i$ of $f$ the following holds:
	- If $H_f(x_i)$ is negative definite, then $x_i$ is a local maximum
	- If $H_f(x_i)$ is positive definite, then $x_i$ is a local minimum
	- If $H_f(x_i)$ is indefinite, then $x_i$ is a saddle point
	- If $H_f(x_i)$ is semi-definite, then nothing can be said about the type of extrema $x_i$ is, based on the Hessian matrix
## Quadrature
- In order to integrate in higher dimensions, the concept of a domain needs to be redefined
#### Standard Domains
- A normal, rectangular domain can be formally defined like so:
$$D = \left \{ (x, y) | a \leq x \leq b, c \leq y \leq d \right \}$$
- Domains with irregular shapes and in multiple dimensions, are modelled like this: 
$$D = \left \{ (x, y) | a \leq x \leq b, l(x) \leq y \leq u(x) \right \}$$
$$D = \left \{ (x, y, z) | a \leq x \leq b, l(x) \leq y \leq u(x), \tilde{l}(x, y) \leq z \leq \tilde{u}(x, y) \right \}$$
###### Illustration
![[Pasted image 20240719174741.png]]
#### Integrating over Standard Domains
- The integral over a standard domain $D$ in $\mathbb{R}^2$ or $\mathbb{R}^3$ can be defined using the intervals and functions, that describe the variables:
$$\int_D f(x, y) \, \mathrm dy \, \mathrm dx = \int_{x = a}^b \int_{y = l(x)}^{u(x)} f(x, y) \, \mathrm dy \, \mathrm dx$$
$$\int_D f(x, y, z) \, \mathrm dz \, \mathrm dy \, \mathrm dx = \int_{x = a}^b \int_{y = l(x)}^{u(x)} \int_{z = \tilde{l}(x, y)}^{\tilde{u}(x, y)} f(x, y, z) \, \mathrm dz \, \mathrm dy \, \mathrm dx$$
- When computing the area, or volume, of a domain $D$ in $\mathbb{R}^2$ or $\mathbb{R}^3$ $f(x, y)$, or $f(x, y, z)$ is set to $1$
#### Integrating under Coordinate Transformations 
- Computing an integral over a standard domain $D$ in $\mathbb{R}^2$ may be very difficult
- In order to still compute the integral, a simpler one, over domain $B$ with different coordinates can be computed and those coordinates can then be transformed into ones from $D$
- The integral over $B$ is computed using the Jacobian of $\phi: B \to D$, which is the function, which transforms the coordinates $x', y'$ from $B$ to $x, y$ in $D$:
$$\int_D f(x, y) \; \mathrm d y \; \mathrm dx = \int_B f(\phi(x', y')) \cdot \mid det(J_{\phi}(x', y')) \mid \; \mathrm d x' \; \mathrm d y'$$
- Again, when computing the area, or volume of a domain, $f(x, y)$ or $f(\phi(x', y')$ can simply be set to $1$