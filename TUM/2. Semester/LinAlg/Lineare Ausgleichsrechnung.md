## Orthogonalraum
- Es sei $V$ ein [[Orthogonalithaet|euklidischer Vektorraum]] mit einem Untervektorraum $U$, wobei gilt $dim(V) = n$, $dim(U) = r$
- Der Orthogonalraum von $U$ wird definiert durch:
$$U^{\perp} = \{v \in V \mid \forall \space u \in U: v \perp u \space \} \leq V$$
- Fuer den Orthogonalraum $U^{\perp}$ gilt:
$$U \cap U^{\perp} = \{0\}$$
$$\forall \space v \in V, \exists_1 \space u \in U, \exists_1 \space u' \in U^{\perp}: v = u + u'$$
$$dim(U^{\perp}) = n - r$$
## Orthogonale Projektion
- Es sei $V = \mathbb{R}^n$ ein und $U \leq V$
- Die orthogonale Projektion $P_U$ wird beschrieben durch:
$$P_U = \begin{cases}
V \rightarrow U \\
v = u + u^{\perp} \mapsto u \\
\end{cases}$$
- Hierbei ist $u$ das Element aus $U$, fuer das die Distanz $||v - u||$ minimal ist
- Es sei $U = \langle b_1, ..., b_r \rangle$ mit $b_i \in \mathbb{R}^n$ und $A = (b_1, ..., b_r) \in \mathbb{R}^{n \times r}$
- $u$ kann somit mithilfe von $Ax$ mit $x \in \mathbb{R}^r$ beschrieben werden
- Ueber ein [[Lineare Gleichungssysteme|lineares Gleichungssystem]] ist $x$ so zu bestimmen, dass $||v - Ax||$ minimal ist
- Fuer $x$ gilt hierbei die Normalengleichung:
$$A^TAx = A^Tv$$
#### Methode der kleinsten Quadrate
- Es sei eine Punktwolke $(x_i, y_i)$ gegeben
- Alle Punkte $(x_i, y_i)$ sollen mithilfe der Funktion $f(x) = \beta_1 f_1(x)+ ... + \beta_r f_r(x)$ moeglichst genau approximiert werden
- Es werden die Matrix $A$, sowie die Vektoren $x$ und $v$ festgelegt, sodass gilt:
$$A = \begin{pmatrix}
f_1(x_1) & ... & f_r(x_1) \\
\vdots & & \vdots \\
f_1(x_n) & ... & f_r(x_n)
\end{pmatrix}$$
$$x = (\beta_1, ..., \beta_r)^T$$
$$v = (y_1, ..., y_n)^T$$
- Mithilfe der Normalengleichung kann nun $x$ so bestimmt werden, dass $||v - Ax||$ minimal ist