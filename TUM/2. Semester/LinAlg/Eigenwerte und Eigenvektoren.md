## Diagonalisierung
- Es sei eine [[Lineare Abbildungen|Abbildung]] $f$ mit $A = {_{E_n}M}(f)_{E_n}$
- Es wird eine [[Basen von Vektorraeumen|Basis]] $B = (b_1, ..., b_n)$ bestimmt, sodass gilt:
$$_BM(f)_B = \begin{pmatrix}
\lambda_1 & & 0 \\
& \ddots  & \\
0 & & \lambda_n
\end{pmatrix}$$
- Man bezeichnet $b_i \neq 0$ als Eigenvektor von $A$ zum Eigenwert $\lambda_i$, falls gilt:
$$Ab_i = \lambda_ib_i$$
#### Bestimmen der Eigenwerte
- Es muss $\lambda$ bestimmt werden, sodass gilt:
$$det(A - \lambda E_N) = 0$$
- Man bezeichnet $det(A - \lambda E_n)$ als charakteristisches Polynom $\chi(\lambda)$ mit der Nullstelle $\lambda$
- Fuer die Eigenwerte $\lambda_i$ gilt:
$$\sum \lambda_i = Spur(A)$$
$$\prod \lambda_i = det(A)$$
#### Bestimmen der Eigenvektoren
- Es sei $\lambda$ als Nullstelle des charakteristischen Polynoms $\chi(\lambda)$ gegeben
- Der Eigenraum zu $\lambda$ ist die Menge der Eigenvektoren und kann mithilfe eines [[Lineare Gleichungssysteme|LGS]] bestimmt werden:
$$Eig_A(\lambda) = \{v \mid (A - \lambda E_n)v = 0\} = Ker(A - \lambda E_n)$$
#### Vielfachheiten
- Die Vielfachheit einer Nullstelle $\lambda$ des charakteristischen Polynoms bezeichnet man als algebraische Vielfachheit $alg(\lambda)$
- Die Anzahl der Eigenvektoren mit Eigenwert $\lambda$ bezeichnet man als geometrische Vielfachheit $geo(\lambda)$
- Die Matrix ist diagonalisierbar, falls algebraische und geometrische Vielfachheit stets gleich sind
## Orthogonales Diagonalisieren
- Ist $A \in \mathbb{R}^{n \times n}$ symmetrisch, so sind die Eigenwerte $\lambda_i$ reell und $B$ ist eine [[Orthogonal- und Orthonormalsystem|Orthonormalbasis]]
- Fuer die Diagonalmatrix $D = {_BM}(f)_B$ gilt somit:
$$D = B^{-1}AB = B^TAB$$
## Gerschgorinkreise
- Die $n$ Eigenwerte einer Matrix $A \in \mathbb{C}^{n \times n}$ liegen in den $n$ Gerschgorinkreisen
- Der $i$-te Gerschgorinkreis wird beschrieben durch:
$$K_i = \{z \in \mathbb{C} \mid |z - a_{i, i}| \leq \sum_{j = 1, \space j \neq i}^{n} |a_{i, j}|\}$$
- Eine Matrix ist invertierbar, falls die $0$ in keinem der Gerschgorinkreise liegt