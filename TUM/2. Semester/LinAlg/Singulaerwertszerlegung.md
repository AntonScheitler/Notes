## Allgemeines
- Zu einer Matrix $A \in \mathbb{R}^{m \times n}$ werden die orthogonalen Matrizen $U \in \mathbb{R}^{m \times m}$ und $V \in \mathbb{R}^{n \times n}$, sowie die Diagonalmatrix $\Sigma \in \mathbb{R}^{m \times n}$ bestimmt, sodass gilt:
$$A = U\Sigma V^T$$
- Falls $m \leq n$, so hat $\Sigma$ das Format:
$$\Sigma = \begin{pmatrix}
\sigma_1 & ... & 0 & 0 & ... & 0 \\
& \ddots & & \vdots & & \vdots \\
0 & ... & \sigma_r & 0 & ... & 0
\end{pmatrix}$$
- Falls $n \leq m$, so hat $\Sigma$ das Format:
$$\Sigma = \begin{pmatrix}
\sigma_1 & & 0 \\
& \ddots & \\
0 & & \sigma_r \\
0 & ... & 0 \\
\vdots & & \vdots \\
0 & ... & 0
\end{pmatrix}$$
- Hierbei ist $r = min\{m, n\}$
#### Bestimmen von $\Sigma$
- Die Eigenwerte $\lambda_1, ..., \lambda_r, ..., \lambda_n$ von $A^TA$ werden bestimmt
- Von den Eigenwerten werden $\lambda_1, ..., \lambda_r$ betrachtet und sortiert
- Fuer die Singulaerwerte $\sigma_i$ von $\Sigma$ gilt:
$$\sigma_i = \sqrt{\lambda_i}$$
#### Bestimmen von V
- Da $A^TA$ symmetrisch ist, bilden die Eigenvektoren $v_1, ..., v_n$ eine [[Orthogonal- und Orthonormalsystem|ONB]]
- Fuer $V$ gilt hierbei:
$$V = (v_1, ..., v_n)$$
#### Bestimmen von U
- Die Vektoren $u_1, ..., u_r$ werden bestimmt ueber:
$$u_i = \frac{1}{\sigma_i}Av_i$$
- Falls $r < m$, werden $u_1, ..., u_r$ mithilfe des [[Orthogonalithaet|Gram-Schmidtverfahrens]] zu einer ONB ergaenzt
- Fuer $U$ gilt hierbei:
$$U = (u_1, ..., u_m)$$