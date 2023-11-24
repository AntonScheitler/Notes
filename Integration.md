## Nummerische Quadratur
- In verschiedenen Anwendungen, ist es wichtig, das Integral einer Funktion $f$ im Intervall $\Omega = [a, b]$ effizient zu ermitteln
#### Berechnung
- Das Integral wird durch eine Summe von Rechtecken approximiert, welche aus den Funktionswerten und den Groessen der Intervallschritte hergeleitet werden:
$$I(f) \approx Q(f) = \sum_{i=0}^ng_i \cdot f(x_i)$$
- Da das Ermitteln der Funktionswerte sehr aufwendig sein kann, kann $f$ durch einen [[Interpolation|Interpolanten]] $g$ in $\Omega$ approximert werden
- Das Integrieren von $d$ in $\Omega$ kann ueber [[Interpolation|Lagrange Polynome]] erfolgen:
$$Q(g) = \int_a^bp(x)\mathrm{d}x = \int_a^b \sum_{i = 0}^n y_i \cdot L_i(x) \mathrm{d}x = \sum_{i=0}^n \Big (\int_a^b y_i \cdot L_i(x) \mathrm{d}x \Big )$$