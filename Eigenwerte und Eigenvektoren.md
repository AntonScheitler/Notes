## Diagonalisierung
- Es sei eine [[Lineare Abbildungen|Abbildung]] $f$ mit $A = {_{E_n}M}(f)_{E_n}$
- Es wird eine [[Basen von Vektorraeumen|Basis]] $B = (b_1, ..., b_n)$ bestimmt, sodass gilt:
$$_BM(f)_B = \begin{pmatrix}
\lambda_1 & & 0 \\
& \ddots  & \\
0 & & \lambda_n
\end{pmatrix}$$
- Man bezeichnet $b_i \neq 0$ als Eigenvektor von $A$ mit Eigenwert $\lambda_i$, falls gilt:
$$Ab_i = \lambda_ib_i$$
#### Bestimmen der Eigenwerte
- Es muss $\lambda$ bestimmt werden, sodass gilt:
$$det(A - \lambda E_N) = 0$$
- Man bezeichnet $det(A - \lambda E_n)$ als charakteristisches Polynom $\chi(\lambda)$ mit der Nullstelle $\lambda$
#### Bestimmen der Eigenvektoren
- Es sei $\lambda$ als Nullstelle des charakteristischen Polynoms $\chi(\lambda)$ gegeben
- Der Eigenraum von $\lambda$ ist die Menge der Eigenvektoren und kann mithilfe eines [[Lineare Gleichungssysteme|LGS]] bestimmt werden:
$$Eig_A(\lambda) = \{v \mid (A - \lambda E_n)v = 0\} = Ker(A - \lambda E_n)$$
#### Vielfachheiten
- Die Vielfachheit einer Nullstelle $\lambda$ des charakteristischen Polynoms bezeichnet man als algebraische Vielfachheit
- Die Anzahl der Eigenvektoren mit Eigenwert $\lambda$ bezeichnet man als geometrische Vielfachheit
- Die Matrix ist diagonalisierbar, falls algebraische und geometrische Vielfachheit stets gleich sind