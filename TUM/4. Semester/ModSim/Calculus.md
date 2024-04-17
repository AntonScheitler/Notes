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