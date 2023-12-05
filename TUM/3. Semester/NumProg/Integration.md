## Das Integrationsproblem
- In verschiedenen Anwendungen, ist es wichtig, das Integral einer Funktion $f$ im Intervall $\Omega = [a, b]$ effizient zu ermitteln
#### Integration mit Interpolanten
- Das Integral wird durch eine Summe von Rechtecken approximiert, welche aus den Funktionswerten und den Groessen der Intervallschritte hergeleitet werden:
$$I(f) \approx Q(f) = \sum_{i=0}^ng_i \cdot f(x_i)$$
- Da das Ermitteln der Funktionswerte sehr aufwendig sein kann, kann $f$ durch einen [[Interpolation|Interpolanten]] $g$ in $\Omega$ approximert werden
- Das Integrieren von $d$ in $\Omega$ kann ueber [[Interpolation|Lagrange Polynome]] erfolgen:
$$Q(g) = \int_a^bp(x)\mathrm{d}x = \int_a^b \sum_{i = 0}^n y_i \cdot L_i(x) \mathrm{d}x = \sum_{i=0}^n \Big (\int_a^b y_i \cdot L_i(x) \mathrm{d}x \Big )$$
#### Einfache Integrationsregeln
- Das Integral von Polynomen mit niedrigem Grad kann leicht approximiert werden
###### Rechteckregel
- Das Integral wird mithilfe eines Rechtecks approximiert:
$$Q_R(f) = (b - a) \cdot f \Big (\frac{a + b}{2} \Big)$$
- Diese Approximation ist fuer Polynome vom Grad $0$ oder $1$ fehlerfrei
###### Trapezregel
- Das Integral kann mithilfe eines Trapez approximiert werden:
$$Q_T(f) = (b-a) \cdot \frac{f(a) + f(b)}{2}$$
- Der Genauigkeitsgrad ist hierbei derselbe wie bei der Rechteckregel
###### Keplersche Regel
- Fuer einen hoeheren Genauigkeitsgrad kann die Keplersche Regel fuer die Integration genutzt werden:
$$Q_F(f) = (b - a) \cdot \frac{f(a) + 4f \Big (\frac{a+b}{2} \Big) + f(b)}{6}$$
- Diese Approximation ist fuer Polynome mit einem Grad von hoechstens 3 fehlerfrei
###### Restglied
- TODO
###### Beispiel
![[Pasted image 20231129184049.png]]
#### Zusammengesetzte Integrationsregeln
- Um Polynome mit hoeherem Grad zu integrieren, koennen Teilintegrale mit einfachen Integrationsregeln berechnet und zu einem Gesamtintegral zusammengefuegt werden
- Das Integrationsintervall wird hierbei in $n$ Teile der Laenge $\frac{b - a}{n}$ aufgeteilt
###### Trapezsumme
- In jedem Teilintervall wird die Trapezregel angewandt und die Ergebnisse summiert:
$$Q_{TS}(f) = \frac{(b - a)}{2} \cdot \Big (\frac{f(x_0)}{2} + f(x_1) + f(x_2) + ... f(x_{n-1})+ \frac{f(x_n)}{2} \Big )$$
###### Simpson Summe
- In jedem Teilintervall wird die Keplersche Regel angewandt und die Ergebnisse summiert:
$$Q_{SS}(f) = \frac{b - a}{6} \cdot \big (f(x_0) + 4f(x_1) + 2f(x_2) + ... + 2f(x_{n-2}) + 4f(x_{n-1}) + f(x_n) \big)$$
## Extrapolation
- Integrationsverfahren fuer Polynome mit hohem Grad koennen aus Verfahren mit niedrigerem Genauigkeitsgrad abgeleitet werden