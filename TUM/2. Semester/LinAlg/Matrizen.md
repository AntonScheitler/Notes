## Aufbau
- Eine Matrix $A$ mit $m$ Zeilen und $n$ Spalten kann folgendermassen beschrieben werden:
$$A = \begin{pmatrix}
a_{11} & ... & a_{1n} \\
\vdots & & \vdots \\
a_{m1} & ... & a_{mn}
\end{pmatrix} = (a_{ij})_{mn}=(a_{ij})$$
- Eine Matrix kann als Sammlung von Spalten und Zeilen betrachtet werden
## Besondere Matrizen
- Eine $m \times n$ Nullmatrix hat folgende Form:
$$0 = \begin{pmatrix}
0 & ... & 0 \\
\vdots & & \vdots \\
0 & ... & 0
\end{pmatrix} \in \mathbb{K}^{m \times n}$$
#### Quadratische Matrizen
- Eine Matrix $A \in \mathbb{K}^{n \times n}$ nennt man quadratisch 
- Diagonalmatrizen werden beschrieben durch:
$$D = \begin{pmatrix}
\lambda_1 & & 0 \\
& \ddots & \\
0 & & \lambda_n
\end{pmatrix} = diag(\lambda_1, ..., \lambda_n)$$
- Eine besondere Form der Diagonalmatrix ist die Einheitsmatrix:
$$E_n = \begin{pmatrix}
1 & & 0 \\
& \ddots & \\
0 & & 1
\end{pmatrix}$$
- Die oberen und unteren Dreiecksmatrizen werden dargestellt durch:
$$O = \begin{pmatrix}
\star & ... & \star \\
& \ddots & \vdots \\
0 & & \star
\end{pmatrix}, U = \begin{pmatrix}
\star & & 0 \\
\vdots & \ddots & \\
\star & ... & \star
\end{pmatrix}$$
###### Elementarmatrizen
- Ueber spezielle Matrizen koennen durch [[Rechnen mit Matrizen|Multiplikation]] die elementaren Zeilenumformungen realisiert werden
- Mithlife von Permutationsmatrizen koennen die Zeilen einer Matrix ausgetauscht werden
$$\begin{pmatrix}
1 & 0 & 0 \\
0 & 0 & 1 \\
0 & 1 & 0
\end{pmatrix} \cdot \begin{pmatrix}
1 & 1 & 1 \\
2 & 2 & 2 \\
3 & 3 & 3
\end{pmatrix} = \begin{pmatrix}
1 & 1 & 1 \\
3 & 3 & 3 \\
2 & 2 & 2
\end{pmatrix}$$
- Eine Zeile einer Matrix kann folgendermassen mit einem $\lambda$ multipliziert werden:
$$\begin{pmatrix}
1 & 0 & 0 \\
0 & e & 0 \\
0 & 0 & 1
\end{pmatrix} \cdot \begin{pmatrix}
1 & 1 & 1 \\
2 & 2 & 2 \\
3 & 3 & 3
\end{pmatrix} = \begin{pmatrix}
1 & 1 & 1 \\
2e & 2e & 2e \\
3 & 3 & 3
\end{pmatrix}$$
- Das Addieren des $\lambda$-fachen einer Zeile auf eine andere Zeile erfolgt durch:
$$\begin{pmatrix}
1 & 0 & 0 \\
0 & 1 & 3 \\
0 & 0 & 1
\end{pmatrix} \cdot \begin{pmatrix}
1 & 1 & 1 \\
2 & 2 & 2 \\
3 & 3 & 3
\end{pmatrix} = \begin{pmatrix}
1 & 1 & 1 \\
11 & 11 & 11 \\
3 & 3 & 3
\end{pmatrix}$$