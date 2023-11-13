## Annaehrungsproblem
- In manchen Problemen ist es von Vorteil, eine komplizierte, oder unbekannte Funktion $f(x)$ mit einem Approximanten $p(x)$ zu approximieren
#### Interpolationsproblem
- Ein Approximant $p(x)$ muss an bestimmten Stuetzpunkte $(x_i, y_i)$ genau $f(x)$ entsprechen
- $p(x)$ ist in diesem Fall ein Interpolant
## Polynomielle Interpolation
- Es bietet sich an, bei der Interpolation, Polynome vom Grad $n$ zu verwenden, die die $n + 1$ Stuetzpunkte $(x_i, y_i)$ durchlaufen
#### Lineares Gleichungssystem
- Jedes Polynom kann dargestellt werden durch:
$$\sum_{i = 0}^{n} a_ig_i(x)$$
- $g_i$ sind hierbei Basisfunktionen, mit welchen das Polynom konstruiert wird
- Die Koeffizienten $a_i$ koennen mithilfe eines [[Lineare Gleichungssysteme|linearen Gleichungssystems]] bestimmt werden
###### Beispiel
$$\begin{pmatrix}
g_0(x_0) & ... & g_n(x_0) \\
\vdots & \ddots & \vdots \\
g_0(x_n) & ... & g_n(x_n)
\end{pmatrix} \cdot \begin{pmatrix}
a_0 \\
\vdots \\
a_n
\end{pmatrix} = \begin{pmatrix}
y_0 \\
\vdots \\
y_n
\end{pmatrix}$$
#### Lagrange Polynome
- Fuer die Lagrange Interpolation dienen die Lagrange Polynome $L_k(x)$ als Basisfunktionen
- Ein Lagrange Polynom $L_k(x)$ mit Grad $n$ kann bestimmt werden ueber:
$$L_k(x) = \prod_{i \neq k}^n \frac{x - x_i}{x_k - x_i}$$
- Hierbei ist zu beachten, dass fuer die Stellen $x_i$ gilt:
$$L_k(x_i) = \begin{cases}
1, & \text{falls } i = k \\
0, & \text{sonst}
\end{cases}$$
- Werden Lagrange Polynome verwendet, so entsprechen die Koeffizienten den Stuetzwerten
$$p(x) = \sum_{k = 0}^{n} y_k \cdot L_k(x)$$
#### Aitken-Neville Verfahren
- Mithilfe des Aitken-Neville Verfahrens kann der Interpolant $p(x)$ an einer bestimmten Stelle $x_j$ ausgewertet werden, ohne, dass die Koeffizienten des Polynoms berechnet werden muessen
- Zur bestimmung von $p(x_j)$ wird ein rekursives Verfahren angewandt:
$$p[i, k] = p[i, k - 1] + \frac{x_j - x_i}{x_{i + k} - x_i} \cdot (p[i + 1, k - 1] - p[i, k - 1])$$
###### Beispiel
![[Pasted image 20231113113035.png]]
#### Newton Verfahren
- Die Koeffizienten $c_{i, k}$ des Polynoms werden rekursiv definiert:
$$c_{i, 0} = f(x_i) = y_i$$
$$c_{i, 1} = \frac{y_{i + 1} - y_i}{x_{i + 1} - x_i}$$
$$c_{i, k} = \frac{c_{i + 1, k - 1} - c_{i, k-1}}{x_{i + k} - x_i}$$
- Das Polynom wird dann gebildet durch:
$$p(x) = \sum_{i = 0}^n c_{0, i} \space \cdot \prod_{k = 0}^{i - 1} x - x_k$$
###### Vorteil
- Muessen zusaetzliche Punkte interpoliert werden, so muss beim Newton Verfahren lediglich ein Summand hinzugefuegt werden
###### Beispiel
![[Pasted image 20231113110446.png]]
#### Runge Effekt
- Bei einer aequidistanten Platzierung der Stuetzpunkte kommt es an den Raendern des betrachteten Intervalls zu grossen Stoerungen
- Stuetzpunkte sollten somit vorwiegend an den Raendern des Intervalls platziert werden
###### Beispiel
![[Pasted image 20231107172438.png]]
## Polynomspline
- Eine Interpolation ist moeglich, indem mehrere Polynome niedrigeren Grades zu einer geeigneten Form zusammengefuegt werden
- Die Polynome werden generell in einem Intervall um einen Stuetzpunkte $(x_i, y_i)$ konstruiert
- Ein Spline der Ordnung $n$ verwendet in jedem Stuetzpunkt ein Polynom vom Grad $n - 1$
#### Konstruktion
- Es muss sichergestellt werden, dass das Gesamtpolynom stetig und differenzierbar ist
- TODO