## Vektoriteration
- Ein beliebiger Vektor $x \in \mathbb{R}^n$ wird als Startwert gewaehlt, wobei $x$ als Linearkombination der Eigenvektoren $u_i$ von $A \in \mathbb{R}^{n \times n}$ dargestellt werden kann
- Somit gilt:
$$Ax = A(c_1u_1 + ... + c_n u_n)$$
$$Ax = \lambda_1c_1u_1 + ... + \lambda_nc_1u_n$$
$$A^kx = \lambda_1^k(c_1u_1 + ... + \Big ( \frac{\lambda_n}{\lambda_1} \Big )^k c_1u_n)$$
- Multipliziert man somit $x$ nur oft genug mit $A$, so erhaelt man ein eine Approximation des Eigenvektors des betragsmaessig groessten Eigenwerts
###### Vorgehen
- Mithilfe eines Startvektors $x^{(0)}$ kann folgendermassen iteriert werden:
- TODO
#### Berechnen des Eigenwerts
- Ist $x$ der approximierte Eigenvektor, so gilt fuer den entsprechenden Eigenwert $\lambda$:
$$\lambda = \frac{x^T A x}{x^T x}$$
#### Bestimmen zusaetzlicher Eigenwerte
- Ist $x_1$ der approximierte Eigenvektor fuer den entsprechenden Eigenwert $\lambda_1$, so kann eine Matrix $A'$ erstellt werden:
$$A' = A - \lambda_1 x_1 x_1^T$$
- $A'$ hat hierbei dieselben Eigenwerte wie $A$, jedoch gilt $\lambda_1 = 0$
- In nachfolgenden Iterationen koennen somit weitere Eigenwerte besitmmt werden
#### Nachteile
- Jede Vektoriteration hat einen Aufwand von $O(n^2)$
#### Inverse Iteration
- Soll der Eigenwert ermittelt werden, dessen Wert nahe einer Schaetzung $\mu$ liegt, so muss $(A - \mu E_n)^{-1}$ in einer Vektoriteration genutzt werden
- Statt das Inverse der Matrix zu berechnen, kann jedoch das Verhalten von $(A - \mu E_n)^{-1}$ ausgenutzt werden
- Hierbei gilt:
$$x^{(k + 1)} = (A - \mu E_n)^{-1} x^{(k)}$$
$$(A - \mu E_n) x^{(k + 1)} = x^{(k)}$$
- Die Approximation $x^{(k+1)}$ des $k+1$-ten Iterationsschritts kann also mithilfe eines linearen Gleichungssystems ermittelt werden
- Der uebrige Verlauf entspricht dem der Vektoriteration
###### Nachteile
- Fuer jeden Iterationsschritt muss ein lineares Gleichungssystem geloest werden
#### Rayleigh Quotient Iteration
- Die Schaetzung $\mu$, die in der inversen Iteration verwendet wird, wird in jedem Schritt vergenauert, indem sie auf die momentane Approximation des Eigenwerts gesetzt wird
- Das Verfahren konvergiert in der Regel schneller
###### Nachteile
- Da sich $\mu^{(k)}$ in jeder Iteration veraendert, kann fuer das Loesen des LGS $(A - \mu^{(k)}E_n)x^{(k + 1)}$ nicht mehr die [[Loesen linearer Gleichungssysteme|LR-Dekomposition]] verwendet werden
## QR Iteration
- Eine Folge $A_k$ von Matrizen wird erzeugt, deren Eigenwerte denen von $A$ entsprechen und die gegen eine Dreiecksmatrix konvergieren
- Wurde die Dreiecksmatrix erreicht, so koennen die Eigenwerte abgelesen werden
#### Vorgehen
- TODO
#### Reduktionsalgorithmus
- Die QR Zerlegung einer Tridiagonalmatrix ist effizient zu realisieren