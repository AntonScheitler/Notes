## Annaehrungsproblem
- In manchen Problemen ist es von Vorteil, eine komplizierte, oder unbekannte Funktion $f(x)$ mit einem Approximanten $p(x)$ zu approximieren
#### Interpolationsproblem
- Ein Approximant $p(x)$ muss an bestimmten Stuetzpunkte $(x_i, y_i)$ genau $f(x)$ entsprechen
- $p(x)$ ist in diesem Fall ein Interpolant
- Alle Interpolationsverfahren liefern denselben Interpolanten und unterscheiden sich nur in dessen Berechnung
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
###### Vorteil
- Es muss kein lineares Gleichungssystem ausgewertet werden, um die Koeffizienten der Polynome zu bestimmen
#### Aitken-Neville Verfahren
- Mithilfe des Aitken-Neville Verfahrens kann der Interpolant $p(x)$ an einer bestimmten Stelle $x_j$ ausgewertet werden
- Zur bestimmung von $p(x_j)$ wird ein rekursives Verfahren angewandt:
$$p[i, 0] = f(x_i) = y_i$$
$$p[i, k] = p[i, k - 1] + \frac{x_j - x_i}{x_{i + k} - x_i} \cdot (p[i + 1, k - 1] - p[i, k - 1])$$
###### Vorteil
- Da das Verfahren den Interpolanten nur auswertet, muessen weder die Koeffizienten noch die Polynome zur Interpolation bestimmt werden
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
#### Kondition
- Muessen viele Punkte interpoliert werden, so ist der Grad des polynomiellen Interpolanten besonders gross
- Das Interpolationsproblem wird hierdurch schlecht konditioniert
- Das Verbessern der Genauigkeit durch das Hinzufuegen zusaetzlicher Stuetzpunkte verschlechtert somit die Kondition
## Hermite-Interpolation
- Eine Interpolation ist moeglich, indem mehrere Polynome niedrigeren Grades zu einer geeigneten Form zusammengefuegt werden
- Die Polynome werden nur in einem Intervall zwischen zwei Stuetzstellen $x_i, x_{i+1}$ konstruiert
- In der Regel werden kubische Funkionen als Intervallfunktion verwendet
#### Herleitung
- Um eine allgemeine Intervallfunktionen zu bestimmen wird zunaechst eine Funktion fuer das Invervall $[0, 1]$ aufgestellt, wodurch sich folgende Basispolynome ergeben
$$H_0(t) = 1 - 3t^2 + 2t^3$$
$$H_1(t) = 3t^2 - 2t^3$$
$$H_2(t) = t - 2t^2 + t^3$$
$$H_3(t) = -t^2 + t^3$$
- Um diese Funktion zu verallgemeinern muessen beliebige $x_i$ und $x_{i + 1}$ mithilfe einer Transformationsfunktion auf das Intervall $[0, 1]$  abgebildet werden:
$$t_i(x) = \frac{x - x_i}{x_{i + 1} - x_i} = \frac{x - x_i}{h_i}$$
- Hierdurch ergibt sich die allgemeine Form der kubischen Intervallfunktion:
$$p_i(t) = y_i H_0(t) + y_{i + 1} H_1(t)+ h_i \cdot (y_i' H_2(t) + y_{i + 1}' H_3(t))$$
#### Polynomsplines
- Um die Ableitungen an den Stuetzpunkten zu bestimmen wird gefordert, dass der Interpolant an jeder Stelle doppelt differenzierbar ist
- Zusaetzlich muessen die Ableitungen zum Start- und Endpunkt muessen gegeben sein, oder werden auf $0$ gesetzt
- Fuer die uebrigen Ableitungen gilt:
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
- Wurden alle Ableitungen bestimmt, so koennen die Polynome in den Intervallen bestimmt werden durch:
$$p_i(t) = y_i H_0(t) + y_{i + 1} H_1(t)+ h_i \cdot (y_i' H_2(t) + y_{i + 1}' H_3(t)), \space \space x_i \leq t \leq x_{i + 1}$$
###### Vorteile
- Das Interpolieren durch Polynomsplines ist deutlich effizienter als jede Form der polynomiellen Interpolation
- Durch Polynomsplines wird der Runge-Effekt verhindert
###### Besonderheiten
- Eine Veraenderung in einem Stuetzpunkt hat bei Polynomsplines nur lokale Auswirkungen
## Methode der kleinsten Quadrate
- Eine Punktwolke wird mit einer linearen Funktion $y = t + mx$ approximiert
- Mithilfe der Punktewolke wird die Matrix $A$ erstellt
- Mithilfe der [[Lineare Ausgleichsrechnung|Normalengleichung]] koennen die Koeffizienten $t$ und $m$ bestimmt werden:
$$A^TAx = A^Tb$$
## Fourier Transformation
- Das Ziel einer Fourier Transformation ist das Unterteilen einer Funktion in ihre Grundfrequenzen
- Insbesondere muss ein Gewichtungsvektor $c$ der Grundfrequenzen bestimmt werden
###### Vorgehen
- Gegeben ist ein Vektor $v$ von Frequenzwerten, sowie $\omega = e^{\frac{2\pi i}{n}}$
- $c$ wird bestimmt ueber:
$$c_k = \frac{1}{n} \cdot \sum_{j=0}^{n-1} v_j \cdot \overline{\omega}^{jk}$$
- Dies wird mit einer Matrix Vektor Multiplikation realisiert:
$$\begin{pmatrix}
c_0 \\
c_1 \\
\vdots \\
c_{n - 1}
\end{pmatrix} = \frac1n \begin{pmatrix}
1 & 1 & 1 & ... & 1 \\
1 & \overline{\omega}^1 & \overline{\omega}^2 & ... & \overline{\omega}^{n-1} \\
\vdots & \vdots & \vdots & \vdots & \vdots \\
1 & \overline{\omega}^{n-1} & \overline{\omega}^{2(n-1)} & ... & \overline{\omega}^{(n-1)(n-1)}
\end{pmatrix} \cdot \begin{pmatrix}
v_0 \\
v_1 \\
\vdots \\
v_{n-1}
\end{pmatrix}$$
## Inverse Fourier Transformation
- Das Ziel einer inversen Fourier Transformation ist das Bestimmen der Frequenzwerte $v$ anhand eines Gewichtungsvektors $c$
#### Diskrete Inverse Fourier Transformation
- Die diskrete inverse Fourier Transformation erfolgt aehnlich zur regulaeren Fourier Transformation
###### Vorgehen
- Gegeben sind ein Gewichtungsvektor $c4, sowie $\omega = e^{\frac{2\pi i}{n}}$
- $v$ wird bestimmt ueber:
$$c_k = \frac{1}{n} \cdot \sum_{j=0}^{n-1} v_j \cdot \omega^{jk}$$
- Dies wird mit einer Matrix Vektor Multiplikation realisiert:
$$\begin{pmatrix}
v_0 \\
v_1 \\
\vdots \\
v_{n - 1}
\end{pmatrix} = \begin{pmatrix}
1 & 1 & 1 & ... & 1 \\
1 & \omega^1 & \omega^2 & ... & \omega^{n-1} \\
\vdots & \vdots & \vdots & \vdots & \vdots \\
1 & \omega^{n-1} & \omega^{2(n-1)} & ... & \omega^{(n-1)(n-1)}
\end{pmatrix} \cdot \begin{pmatrix}
c_0 \\
c_1 \\
\vdots \\
c_{n-1}
\end{pmatrix}$$
#### Schnelle Inverse Fourier Transformation
- Die schnelle inverse Fourier Transformation liefert dieselben Ergebnisse wie die diskrete, ist jedoch deutlich effizienter
###### Vorgehen
- Die schnelle inverse Fourier Transformation wird in eine Sortier- und eine Kombinierphase eingeteilt
###### Sortierphase
- In der Sortierphase werden Vektoren anhand der Paritaet der Indizes ihrer Elemente aufgeteilt
###### Kombinierphase
- In der Kombinierphase werden die Elemente eines Vektors in Bloecke gruppiert, wobei sich die Groesse der Bloecke in jedem Schritt verdoppelt
- Die Elemente eines Blocks werden paarweise ueber den Butterfly-Operator kombiniert
- Elementenpaare eines Blocks werden aufsteigend ueber den Index $j$ indiziert
###### Butterfly-Operator
![[Pasted image 20231128091239.png]]
###### Beispiel
![[Pasted image 20240201141432.png]]