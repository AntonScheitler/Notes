## Skalarprodukt
- Es wird eine Abbildung $\langle \cdot, \cdot \rangle$ wird definiert durch:
$$\langle \cdot, \cdot \rangle: \begin{cases}
V \times V \rightarrow \mathbb{R} \\
(v, w) \mapsto \langle v, w \rangle \\
\end{cases}$$
- Diese Abbildung bezeichnet man als Skalarprodukt, falls sie bilinear, symmetrisch und positiv definit ist:
$$\forall \space v, v', w, \in V: \forall \space \lambda \in \mathbb{R}: \langle \lambda v + v', w \rangle = \lambda \langle v, w \rangle + \langle v', w \rangle$$
$$\forall \space v, w \in V: \langle v, w \rangle = \langle w, v \rangle$$
$$\forall \space v \in V: \langle v, v \rangle \geq 0$$
$$\forall v \in V: \langle v, v \rangle = 0 \equiv v = 0$$
#### Euklidische Vektorraeume
- Ist $\langle \cdot, \cdot \rangle$ ein Skalarprodukt ueber $V$, so bezeichnet man $(V, \langle \cdot, \cdot \rangle)$ als euklidischen Vektorraum
- Fuer ein beliebiges $v \in V$ wird die Norm definiert durch:
$$||v|| = \sqrt{\langle v, v \rangle}$$
- Die Distanz zwischen beliebigen $v, w \in V$ wird beschrieben mit:
$$d(v, w) = ||v - w||$$
- Der Winkel zwischen beliebigen $v, w \in V$ wird definiert durch:
$$\alpha = arccos \frac{\langle v, w \rangle}{||v|| \cdot ||w||}$$
- Zwei beliebige $v, w \in V$ sind somit orthogonal, falls gilt:
$$\langle v, w \rangle = 0$$
## Orthogonalsystem
- Es sei $(V, \langle \cdot, \cdot \rangle)$ ein beliebiger euklidischer Vektorraum
- $B \subseteq V$ ist ein Orthogonalsystem, falls gilt:
$$TODO$$
- TODO
#### Normieren
- Es sei $v \in V \setminus \{0\}$
- Die Laenge von $v$ kann auf $1$ normiert werden ueber:
$$v' = \frac{1}{||v||} \cdot v$$
#### Orthogonale Zerlegung
- Es seien $a, v \in V$ beliebig
- Es werden zwei Vektoren $v_a, v_{a^{\perp}}$ bestimmit, sodass gilt:
$$v = v_a + v_{a^{\perp}}$$
$$v_a = \frac{\langle v, a \rangle}{\langle a, a \rangle}a$$
$$v_{a^{\perp}} = v - v_a$$
- Man bezeichnet somit $v = v_a + v_{a^{\perp}}$ als orthogonale Zerlegung von $v$ laengs $a$
#### Linearkombination einer Orthonormalbasis
- Ist $\{b_1, b_2, b_3\}$ eine Orthonormalbasis, so kann die Linearkombination $\lambda_1 b_1 + \lambda_2 b_2 + \lambda_3 b_3$ eines beliebigen $v$ bestimmt werden durch:
$$\lambda_i = \langle b_i, v \rangle$$
#### Orthonormalisierungsverfahren
- TODO
## Orthogonale Matrizen
- Eine Matrix $A \in \mathbb{R}^{n \times n}$ ist orthogonal, falls gilt:
$$A^TA = E_n$$
- Hieraus folgt:
$$S_iS_j = \begin{cases}
1 & \text{, falls } i = j \\
0 & \text{, falls } i \neq j \\
\end{cases}$$
- Die Menge der Spalten $\{S_1, ..., S_n\}$ bildet somit eine Orthonormalbasis
- TODO
#### Eigenschaften
- Fuer jede orthogonale Matrix $A$ gilt:
$$|det(A)| = 1$$
$$A^{-1} = A^T$$
$$TODO$$