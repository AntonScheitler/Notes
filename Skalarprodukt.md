## Allgemeines
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