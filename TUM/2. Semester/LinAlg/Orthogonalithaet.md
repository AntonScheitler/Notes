## Euklidische Vektorraeume
- Ist $\langle \cdot, \cdot \rangle$ ein [[Skalarprodukt]] ueber $V$, so bezeichnet man $(V, \langle \cdot, \cdot \rangle)$ als euklidischen Vektorraum
- Fuer ein beliebiges $v \in V$ wird die Norm definiert durch:
$$||v|| = \sqrt{\langle v, v \rangle}$$
- Die Distanz zwischen beliebigen $v, w \in V$ wird beschrieben mit:
$$d(v, w) = ||v - w||$$
- Der Winkel zwischen beliebigen $v, w \in V$ wird definiert durch:
$$\alpha = arccos \frac{\langle v, w \rangle}{||v|| \cdot ||w||}$$
- Zwei beliebige $v, w \in V$ sind somit orthogonal, falls gilt:
$$\langle v, w \rangle = 0$$
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
## Anwendung von Orthogonalitaet
#### Gram-Schmidtverfahren
- Eine beliebige Basis $\{a_1, ..., a_n\}$ kann folgendermassen in eine [[Orthogonal- und Orthonormalsystem|Orthonormalbasis]] $\{b_1, ..., b_n\}$ ueberfuehrt werden: 
$$b_1 = \frac{1}{||a_1||}a_1$$
$$b_2 = \frac{1}{||c_2||}c_2 \text{, mit } c_2 = a_2 - \langle b_1, a_2 \rangle b_1$$
$$b_3 = \frac{1}{||c_3||}c3 \text{, mit } c_3 = a_3 - \langle b_2, a_3 \rangle b_2 - \langle b_1, a_3 \rangle b_1$$
$$...$$
#### Linearkombination einer Orthonormalbasis
- Ist $\{b_1, b_2, b_3\}$ eine [[Orthogonal- und Orthonormalsystem|Orthonormalbasis]], so kann die Linearkombination $\lambda_1 b_1 + \lambda_2 b_2 + \lambda_3 b_3$ eines beliebigen $v$ bestimmt werden durch:
$$\lambda_i = \langle b_i, v \rangle$$
## Orthogonale Matrizen
- Eine Matrix $A \in \mathbb{R}^{n \times n}$ ist orthogonal, falls gilt:
$$A^TA = E_n$$
- Hieraus folgt:
$$S_iS_j = \begin{cases}
1 & \text{, falls } i = j \\
0 & \text{, falls } i \neq j \\
\end{cases}$$
- Die Menge der Spalten $\{S_1, ..., S_n\}$ bildet somit eine [[Orthogonal- und Orthonormalsystem|Orthonormalbasis]] von $\mathbb{R}^n$
#### Eigenschaften
- Fuer jede orthogonale Matrix $A$ gilt:
$$|det(A)| = 1$$
$$A^{-1} = A^T$$
$$\forall \space v \in \mathbb{R}^n: ||Av|| = ||v||$$