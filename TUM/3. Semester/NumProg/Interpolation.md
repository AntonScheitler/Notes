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
- Bei einer aequidistanten Platzierung vieler Stuetzpunkte kommt es an den Raendern des betrachteten Intervalls zu grossen Stoerungen
- Stuetzpunkte sollten somit vorwiegend an den Raendern des Intervalls platziert werden
###### Beispiel
![[Pasted image 20231107172438.png]]
## Hermite-Interpolation
- Eine Interpolation ist moeglich, indem mehrere Polynome niedrigeren Grades zu einer geeigneten Form zusammengefuegt werden
- Die Polynome werden nur in einem Intervall zwischen zwei Stuetzstellen $x_i, x_{i+1}$ konstruiert
- Ein Interpolatn der Ordnung $n$ verwendet in jedem Stuetzpunkt ein Polynom vom Grad $n - 1$
- In der Regel werden kubische Funkionen als Intervallfunktion verwendet
#### Konstruktion
- Es muss sichergestellt werden, dass das Gesamtpolynom stetig und differenzierbar ist
- Eine Funktion muss somit an ihren Intervallgrenzen sowohl mit den Werten $y_i, y_{i+1}$ als auch den Ableitungswerten $y_i', y_{i+1}'$ uebereinstimmen
- Die Koeffizienten der kubischen Intervallfunktion koennen somit mithilfe eines [[Lineare Gleichungssysteme|linearen Gleichungssystems]] bestimmt werden
- Eine Intervallfunktion in Abhaengigkeit von $y_i, y_i', y_{i + 1}, y_{i + 1}'$ lautet somit:
			$$p_i(t) = y_i(1 - 3t^2 + 2t^3) + y_{i + 1}(3t^2 - 2t^3) + h_i \cdot (y_i'(t - 2t^2 + t^3) + y_{i + 1}'(-t^2 + t^3)$$
###### Transormation
- Um die Koeffizienten effizient fuer jedes Intervall zu berechnen, werden die Koeffizienten im Intervall $[0, 1]$ in Abhaengigkeit von $y_0, y_0', y_1, y_1'$ ermittelt
- Um eine Stelle eines beliebigen Intervalls $[x_i, x_{i+1}]$ in eine Stelle im Intervall $[0, 1]$ zu uebersetzen, wird eine Transformationsfunktion verwendet:
$$h_i = x_{i+1} - x_i$$
$$t_i(x) = \frac{x - x_i}{h_i}$$
#### Vorteil
- Durch die stueckweise Interpolation wird der Runge-Effekt verhindert
#### Polynomsplines
- Um zusaetzlich die zweifache Differenzierbarkeit des Interpolaten zu garantieren, werden Polynomsplines konstruiert
- Aus $p_i''(1) = p_{i + 1}''(0)$ laesst sich herleiten:
$$\begin{pmatrix}
4 & 1 & & & \\
1 & 4 & \ddots & \\
& \ddots & \ddots & 1 \\
& & 1 & 4
\end{pmatrix} \begin{pmatrix}
y_1' \\ y_2' \\ \vdots \\ y_{n - 2}' \\ y_{n - 1}'
\end{pmatrix} = \frac{3}{h} \begin{pmatrix}
y_2 - y_0 \\ y_3 - y_1 \\
\vdots \\
y_{n - 1} - y_{n - 3} \\ y_n - y_{n - 2} 
\end{pmatrix} - \begin{pmatrix}
y_0' \\ 0 \\
\vdots \\
0 \\ y_n'
\end{pmatrix}$$
- Hierdurch lassen sich die Ableitungswerte $y_i'$ bestimmen und die Intervallfunktionen ermitteln
## Methode der kleinsten Quadrate
- Eine Punktwolke wird mit einer Menge von Basisfunktionen $\phi_i$ approximiert
- Mithilfe dieser Basisfunktionen wird die Matrix $A$ erstellt
- Mithilfe der [[Lineare Ausgleichsrechnung|Methode der kleinsten Quadrate]] koennen die Koeffizienten von $\phi_i$ bestimmt werden
## Trigonometrische Interpolation
- Es ist eine Menge von Punkten auf dem Einheitskreis gegeben
- Mithilfe einer  [[Erzeugendensysteme|Linearkombination]] aus Exponentialfunktionen kann diese Punktmenge interpoliert werden
#### Fourier Transformation
- TODO