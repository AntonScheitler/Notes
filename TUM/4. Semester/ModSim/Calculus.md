## Fundamentals
- Existing concepts, like domains and continuity need to be redefined, when dealing with multiple variables
#### Domains
- A point $x_0 \in \mathbb{R}^n$ is considered an inner point of a domain $D \subseteq \mathbb{R}^n$, if there is sphere centered around $x_0$, which fully lies in $D$:
$$\exists \space \varepsilon \in \mathbb{R}: B_{\varepsilon}(x_0) = \left \{ x \in \mathbb{R}^n \mid ||x - x_0|| < \varepsilon \right \} \subseteq D$$
- The set $\dot{D}$ of all inner points of $D$ is called the interior of $D$
- A point $x_0 \in \mathbb{R}^n$ is considered a boundary point of $D \subseteq \mathbb{R}^n$, if it lies directly on the surface of the sphere of $D$:
$$B_{\varepsilon}(x_0) \cap D \neq \emptyset \space \text{and} \space B_{\varepsilon}(x_0) \cap (D^C) \neq \emptyset, \space \text{where} \space D^C = \mathbb{R}^n \setminus D$$
- The set $\partial D$ of all boundary points of $D$ is called the boundary of $D$
- The set $\overline{D} = D \cup \partial D$ is called the closure of $D$
###### Types
- $D$ is closed, if $D = \overline{D}$
- $D$ is bounded, if all vectors in $D$ have a limited length
- $D$ is compact, if it is closed and bounded
#### Partial Differentiation
- When dealing with multiple variables, a function needs to be partially derived with respect to individual variables
- The partial derivative of a function $f$ with respect to the variable $x_i$ is written as $f_{x_i}$
###### Gradient
- The gradient of a function at a point $a$ is defined as:
$$\nabla f(a) = \begin{pmatrix}
f_{x_1}(a) \\
\vdots \\
f_{x_n}(a) \\
\end{pmatrix}$$
- This vector represents the steepest ascent from $a$
- As a result, the steepest ascent from $a$ is represented by $- \nabla f(a)$
###### Hessian Matrix
- The hessian matrix of $f$ is defined using its second partial derivatives:
$$H_f(x) = \begin{pmatrix}
f_{x_1 x_1}(x) & ... & f_{x_1 x_n}(x) \\
\vdots & & \vdots \\
f_{x_n x_1}(x) & ... & f_{x_n x_n}(x) \\
\end{pmatrix}$$
###### Jacobian Matrix
- A jacobian matrix $Df(x)$ is needed, in order to define the partial derivative of a function $f$ with the form:
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
- In order to find all extrema of a function $f: D \subseteq \mathbb{R}^n = \mathbb{R}$, the root of its gradient needs to be determined
- All points $x_i$ with $\nabla f(x_i) = 0$ are called critical points of $f$
#### Types of extrema
- For a critical point $x_i$ of $f$ the following holds:
	- If $H_f(x_i)$ is negative definite, then $x_i$ is a local maximum
	- If $H_f(x_i)$ is positive definite, then $x_i$ is a local minimum
	- If $H_f(x_i)$ is indefinite, then $x_i$ is a saddle point
	- If $H_f(x_i)$ is semi-definite, then nothing can be said about the type of extrema $x_i$ is
## Quadrature
- In order to integrate in higher dimensions, the concept of a domain needs to be redefined
#### Standard Domains
- A normal, rectangular domain can be formally defined like so:
$$D = \left \{ (x, y) | a \leq x \leq b, c \leq y \leq d \right \}$$
- In order to describe standard domains with irregular shapes and in multiple dimensions, the following approach is used:
$$D = \left \{ (x, y) | a \leq x \leq b, l(x) \leq y \leq u(x) \right \}$$
$$D = \left \{ (x, y, z) | a \leq x \leq b, l(x) \leq y \leq u(x), \tilde{l}(x, y) \leq z \leq \tilde{u}(x, y) \right \}$$
#### Integrating
- The integral over a standard domain $D$ in $\mathbb{R}^2$ or $\mathbb{R}^3$ can be defined as follows:
$$\int\int_D f(x, y) \, \mathrm dy \, \mathrm dx = \int_{x = a}^b \int_{y = l(x)}^{u(x)} f(x, y) \, \mathrm dy \, \mathrm dx$$
$$\int \int \int_D f(x, y, z) \, \mathrm dz \, \mathrm dy \, \mathrm dx = \int_{x = a}^b \int_{y = l(x)}^{u(x)} \int_{z = \tilde{l}(x, y)}^{\tilde{u}(x, y)} f(x, y, z) \, \mathrm dz \, \mathrm dy \, \mathrm dx$$
###### Area and Volume
- The area, or volume, of a domain $D$ in $\mathbb{R}^2$ or $\mathbb{R}^3$ can be computed by using $f(x, y) = 1$, or $f(x, y, z) = 1$ in the integration of $D$
## Partial Differential Equations
- In a partial differential equation, a function $u$ is defined using an equation, which includes partial derivatives of itself
#### Types of PDEs
- PDEs can have different orders
###### First Order PDE
- In a first order PDE, the coefficients of $u$ and those of its derivatives are all constant
###### Second Order PDE
- In a second order PDE, $u$ and its derivatives appear only in the first power and not inside nonlinear functions