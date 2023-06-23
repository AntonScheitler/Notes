## Rechenoperationen
- Auf [[Matrizen]] werden unterschiedliche Operationen definiert
#### Transponieren
- Es sei $A = (a_{ij}) \in \mathbb{K}^{n \times m}$ eine beliebige Matrix
- Man bezeichnet $A^T$ als die zu $A$ transponierte Matrix:
$$A = \begin{pmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 0
\end{pmatrix}, A^T = \begin{pmatrix}
1 & 4 & 7 \\
2 & 5 & 8 \\
3 & 6 & 0
\end{pmatrix}$$
- Falls $A = A^T$, nennt man $A$ eine symmetrische Matrix
- Fuer $A, B \in \mathbb{K}^{m \times n}$ und $\lambda \in \mathbb{K}$ gilt:
$$(A + B)^T = A^T + B^T$$
$$(\lambda A)^T = \lambda A^T$$
$$(AB)^T = B^TA^T$$

#### Addition
- Es seien $A = (a_{ij}), B = (b_{ij}) \in \mathbb{K}^{n \times m}$ beliebige Matrizen
- $A + B$ beschreibt die Addition dieser Matrizen:
$$
A + B = \begin{pmatrix}
a_{11} & ... & a_{1n} \\
\vdots & & \vdots \\
a_{m1} & ... & a_{mn}
\end{pmatrix} + \begin{pmatrix}
b_{11} & ... & b_{1n} \\
\vdots & & \vdots \\
b_{m1} & ... & b_{mn}
\end{pmatrix} = \begin{pmatrix}
a_{11} + b_{11} & ... & a_{1n} + b_{1n} \\
\vdots & & \vdots \\
a_{m1} + b_{m1} & ... & a_{mn} + b_{mn}
\end{pmatrix}$$
#### Skalare Multiplikation
- Es seien $A = (a_{ij}) \in \mathbb{K}^{n \times m}$ und $\lambda \in \mathbb{K}$ beliebig
- Die skalare Multiplikation von $A$ mit $\lambda$ erfolgt folgendermassen:
$$\lambda \cdot \begin{pmatrix}
a_{11} & ... & a_{1n} \\
\vdots & & \vdots \\
a_{m1} & ... & a_{mn}
\end{pmatrix} = \begin{pmatrix}
\lambda a_{11} & ... & \lambda a_{1n} \\
\vdots & & \vdots \\
\lambda a_{m1} & ... & \lambda a_{mn}
\end{pmatrix}$$
#### Matrix Multiplikation
- Die Multiplikation zweier Matrizen $A = (a_{ij}) \in \mathbb{K}^{m \times n}$ und $B = (b_{ij}) \in \mathbb{K}^{n \times p}$ wird beschrieben durch:
$$A \cdot B = \begin{pmatrix}
z_1 \\
\vdots \\
z_m
\end{pmatrix} \cdot \begin{pmatrix}
s_1 & ... & s_p
\end{pmatrix} = \begin{pmatrix}
z_1 \cdot s_1 & ... & z_1 \cdot s_p \\
\vdots & & \vdots \\
z_m \cdot s_1 & ... & z_m \cdot s_p
\end{pmatrix}$$
- $z_1, ..., z_m$ sind hierbei die Zeilen von $A$ und $s_1, ..., s_p$ die Spalten von $B$
- Fuer das Ergebnis der Multiplikation gilt somit:
$$A \cdot B \in \mathbb{K}^{m \times p}$$
- Zudem gilt fuer eine beliebige Matrix $A \in \mathbb{K}^{n \times n}$:
$$A^0 = E_n$$
###### Neutrales Element
- Das neutrale Element bezueglich der Multiplikation ist die [[Matrizen|Einheitsmatrix]] $E_n$
## Invertieren von Matrizen
- Eine quadratische Matrix $A \in \mathbb{K}^{n \times n}$ hat ein Inverses $A^{-1}$, falls $rg(A) = n$ gilt
- Fuer zwei Matrizen $A, B \in \mathbb{K}^{n \times n}$ gilt:
$$(AB)^{-1} = B^{-1}A^{-1}$$
#### Bestimmen des Inversen
- Das Inverse einer Matrix $A$ kann mithilfe eines [[Lineare Gleichungssysteme|LGS]] ermittelt werden
	- Die erweiterte Koeffizientenmatrix $(A|E_n)$ wird notiert
	- Elementare Zeilenumformungen werden ausgefuehrt, sodass $E_n$ auf der linken Seite steht: $$(A|E_n) \leadsto ... \leadsto (E_n|A^{-1})$$
	 - Das Inverse kann nun abgelesen werden
