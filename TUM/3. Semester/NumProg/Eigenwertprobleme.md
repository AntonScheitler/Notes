## Vektoriteration
- Mithilfe von Vektoriterationen koennen nacheinander Eigenvektoren und ihre entsprechenden Eigenwerte ermittelt werden
#### Power Iteration
- Ein beliebiger Vektor $x \in \mathbb{R}^n$ wird als Startwert gewaehlt, wobei $x$ als Linearkombination der Eigenvektoren $u_i$ von $A \in \mathbb{R}^{n \times n}$ dargestellt werden kann
- Somit gilt:
$$Ax = A(c_1u_1 + ... + c_n u_n)$$
$$Ax = \lambda_1c_1u_1 + ... + \lambda_nc_1u_n$$
$$A^kx = \lambda_1^k(c_1u_1 + ... + \Big ( \frac{\lambda_n}{\lambda_1} \Big )^k c_1u_n)$$
- Multipliziert man somit $x$ nur oft genug mit $A$, so erhaelt man ein eine Approximation des Eigenvektors des betragsmaessig groessten Eigenwerts
###### Vorgehen
- Mithilfe eines Startvektors $x^{(0)}$, mit $|| x^{(0)} || = 1$ kann folgendermassen iteriert werden:
	1. $w^{(k)} = A x^{(k)}$
	2. $\lambda^{(k)} = (x^{(k)})^T w^{(k)}$
	3. $x^{(k + 1)} = \frac{w^{(k)}}{||w^{(k)}||}$
- $x^{(k)}$ und $\lambda^{(k)}$ sind hierbei die Approximationen des groessten Eigenwerts und des entsprechenden Eigenvektors im $k$-ten Schritt
###### Rayleigh Quotient
- Ist $x$ der approximierte Eigenvektor, so gilt fuer den entsprechenden Eigenwert $\lambda$:
$$\lambda = \frac{x^T A x}{x^T x}$$
###### Bestimmen zusaetzlicher Eigenwerte
- Ist $x_1$ der approximierte Eigenvektor fuer den entsprechenden Eigenwert $\lambda_1$, so kann eine Matrix $A'$ erstellt werden:
$$A' = A - \lambda_1 x_1 x_1^T$$
- $A'$ hat hierbei dieselben Eigenwerte wie $A$, jedoch gilt $\lambda_1 = 0$
- In nachfolgenden Iterationen koennen somit weitere Eigenwerte besitmmt werden
###### Nachteile
- Jede Vektoriteration hat wegen der Matrix-Vektor Multiplikation einen Aufwand von $O(n^2)$
#### Inverse Iteration
- Soll der Eigenwert ermittelt werden, dessen Wert nahe einer Schaetzung $\mu$ liegt, so muss $(A - \mu E_n)^{-1}$ anstelle von $A$ in einer Vektoriteration genutzt werden
- $A$ wird hierdurch so veraendert, dass ihr groesster Eigenwert nun nahe $\mu$ liegt
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
#### Kondition
- Das Bestimmen von Eigenwerten ist gut konditioniert, das von Eigenvektoren ist schlecht konditioniert
- Die Kondition einer Matrix wird mithilfe ihrer Spektralnorm bestimmt:
$$cond(A) = ||A||_2 \cdot ||A^{-1}||_2$$
$$||A||_2 = max | \sqrt{\lambda_i(A^TA)} |$$
- Fuer symmetrische Matrizen gilt somit:
$$||A||_2 = max | \lambda_i(A) |$$
$$cond(A) = \frac{max | \lambda_i(A) |}{min | \lambda_i(A) |} $$
## QR Iteration
- Eine Folge $A^{(i)}$ von Matrizen wird erzeugt, deren Eigenwerte denen von $A$ entsprechen und die gegen eine Dreiecksmatrix konvergieren
- Wurde die Dreiecksmatrix erreicht, so koennen die Eigenwerte abgelesen werden
#### Vorgehen
- Es wird wiederholt die [[Loesen linearer Gleichungssysteme|QR Zerlegung]] von $A^{(i)}$ ermittelt, um $A^{(i + 1)}$ zu bestimmen:
	1. $A^{(i)} = QR$
	2. $A^{(i + 1)} = RQ$
	3. Falls, die Eintraege ueber der Diagonalen von $A^{(i + 1)}$ klein genug sind, ist die Iteration beendet und die Eigenwerte koennen abgelesen werden
#### Kosten
- Ein Iterationsschritt in der QR Iteration laeuft in $O(n^3)$
#### Reduktionsalgorithmus
- $A$ wird in eine Tridiagonalmatrix umgewandelt
- Die QR Zerlegung der Tridiagonalform von $A$ kann deutlich effizienter realisiert werden als die von $A$ selbst
###### Kosten
- Das Umwandeln von $A$ in eine Tridiagonalmatrix laeuft in $O(n^3)$, ein Schritt in der QR Iteration laeuft hierdurch jedoch in $O(n^2)$