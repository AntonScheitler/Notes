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