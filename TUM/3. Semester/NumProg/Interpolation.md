## Annaehrungsproblem
- In manchen Problemen ist es von Vorteil, eine komplizierte, oder unbekannte Funktion $f(x)$ mit einem Approximanten $p(x)$ zu approximieren
#### Interpolationsproblem
- Ein Approximant $p(x)$ muss an bestimmten Stuetzpunkte $(x_i, y_i)$ genau $f(x)$ entsprechen
- $p(x)$ ist in diesem Fall ein Interpolant
## Polynomielle Interpolation
- Es bietet sich an, bei der Interpolation, Polynome zu verwenden, die die Stuetzpunkte $(x_i, y_i)$ durchlaufen
#### Lagrange Polynome
- Das Lagrange Polynom $L_k(x)$ mit Grad $n$ kann bestimmt werden ueber:
$$L_k(x) = \prod_{i \neq k} \frac{x - x_i}{x_k - x_i}$$
- Hierbei ist zu beachten, dass fuer die Stellen $x_i$ gilt:
$$L_k(x_i) = \begin{cases}
1, & \text{falls } i = k \\
0, & \text{sonst}
\end{cases}$$
- Aus dem Lagrange Polynom kann der Interpolant hergeleitet werden:
$$p(x) = \sum_{k = 0}^{n} y_k \cdot L_k(x)$$
###### Beispiel
![[Pasted image 20231102170305.png]]
#### Aitken-Neville Verfahren
- TODO
#### Newton Verfahren
- Die Koeffizienten $c_{i, k}$ des Polynoms werden rekursiv definiert:
$$c_{i, k} = \frac{c_{i + 1, k - 1} - c_{i, k-1}}{x_{i + k} - x_i}$$
$$c_{i, 0} = f(x_i) = y_i$$
$$c_{i, 1} = \frac{y_{i + 1} - y_i}{x_{i + 1} - x_i}$$
- Das Polynom wird dann gebildet durch:
$$p(x) = \sum_{i = 0}^n c_{0, i} \space \cdot \prod_{k = 0}^{i - 1} x - x_k$$