## Allgemeines
- Es sei $\mathbb{K}$ ein [[Algebraische Strukturen|Koerper]]
- Man bezeichnet $V$ als ein $\mathbb{K}$-Vekorraum, falls $(V, +)$ eine abelsche Gruppe bildet und fuer beliebige Vektoren $u, v \in V$ und Skalare $\lambda, \mu \in K$ gilt:
$$\lambda(u + v) = \lambda u + \lambda v$$
$$(\lambda + \mu)u = \lambda u + \mu u$$
$$(\lambda \mu)u = \lambda (\mu u)$$
$$1 \cdot u = u$$
#### Untervektorraeume
- Es sei $V$ ein $\mathbb{K}$-Vektorraum und $U \subseteq V$, so ist $U$ ein Untervektorraum von $V$, falls gilt:
$$0 \in U$$
$$\forall \space u, v \in U: u + v \in U$$
$$\forall \space u \in U, \lambda \in \mathbb{K}: \lambda u \in U$$
## Beispiele
- Die Menge aller Spaltenvektoren $\mathbb{K}^n$, sowie die Menge aller $n \times m$ Matrizen $\mathbb{K}^{n \times m}$ bilden Vektorraeume
- Die Menge aller Polynome $\mathbb{K}[X]$ ist ebenfalls ein Vektorraum
- Der Vektorraum $\mathbb{K}^M$ wird folgendermassen gebildet:
	$$\mathbb{K}^M = \{f \mid f: M \rightarrow \mathbb{K}\}$$
	 - Es werden folgende Operationen definiert:
	$$f + g : \begin{cases}
	M & \rightarrow & \mathbb{K} \\
	x &\rightarrow & f(x) + g(x) \\
	\end{cases}$$
	$$\lambda \cdot f : \begin{cases}
	M & \rightarrow & \mathbb{K} \\
	x & \rightarrow & \lambda f(x) \\
	\end{cases}$$
	 - Der Vektorraum enthaelt zudem die Nullabbildung:
	$$0 : \begin{cases}
	M & \rightarrow & \mathbb{K} \\
	x & \rightarrow & 0 \\
	\end{cases}$$
	 - Jede Abbildung des Vektorraums besitzt ein Inverses:
	$$f : \begin{cases}
	M & \rightarrow & \mathbb{K} \\
	x & \rightarrow & f(x) \\
	\end{cases} \Rightarrow 
	-f: \begin{cases}
	M & \rightarrow & \mathbb{K} \\
	x & \rightarrow & -f(x) \\
	\end{cases}$$
 