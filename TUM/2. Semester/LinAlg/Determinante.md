## Symmetrische Gruppe
- Es sei die Menge an Abbildungen $S_n$ definiert durch:
$$S_n = \{ \sigma : \{1, ..., n\} \rightarrow \{1, ..., n\} \mid \sigma \text{ ist Bijektion} \}$$
- $\sigma$ sind hierbei Permutationen
- Fuer die Kardinalitaet von $S_n$ gilt:
$$|S_n| = n!$$
- $(S_n, \circ)$ bildet hierbei die symmetrische Gruppe
#### Fehlstaende
- $(j, i)$ ist ein Fehlstand der Permutation $\sigma$, falls gilt:
$$i < j, \space \sigma(i) > \sigma(j)$$
- $f$ beschreibt die Anzahl der Fehlstaende von $\sigma$
#### Signum
- Das Signum einer Permutation $\sigma$ mit $f$ Fehlstaenden wird beschrieben durch:
$$sng(\sigma) = (-1)^f$$
## Determinante einer Matrix
- Fuer jede quadratische Matrix $A \in \mathbb{K}^{n \times n}$ wird die Determinante von $A$ definiert durch:
$$|A| = det(A) = \sum_{\sigma \in S_n} sgn(\sigma) \prod_{i = 1}^{n} a_{i\sigma(i)}$$
- Eine Matrix $A$ ist genau dann invertierbar, falls $det(A) \neq 0$ ist
#### Umformungen
- Fuer zwei beliebige Matrizen $A, B \in \mathbb{K}^{n \times n}$ gilt:
$$det(AB) = det(A) \cdot det(B)$$
- Fuer das Transponierte und die $k$-te Potenz einer Matrix $A \in \mathbb{K}^{n \times n}$ gilt:
$$det(A) = det(A^T)$$
$$det(A^k) = det(A)^k$$

- Durch das Addieren des $\lambda$-fachen einer Zeile zu einer anderen Zeilen aendert sich die Determinante nicht
###### Laplace Entwicklung
- Fuer die Entwicklung nach der $i$-ten Zeile gilt:
$$det(A) = \sum_{j=1}^n(-1)^{i + j} \cdot a_{ij} \cdot det(A_{ij})$$
- Fuer die Entwicklung nach der $j$-ten Spalte gilt:
$$det(A) = \sum_{i=1}^n(-1)^{i + j} \cdot a_{ij} \cdot det(A_{ij})$$