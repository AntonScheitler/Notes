## Grundlagen der Polardarstellung
- Die komplexen Zahlen bilden die [[Konstruktion der komplexen Zahlen|Gausssche Zahlenebene]] und koennen alternativ zur kartesischen Darstellung $(a, b)$ mithilfe von Polarkoordinaten dargestellt werden
- Eine Zahl z wird durch ihre Laenge  $r = |z|$ und ihr Argument, den Winkel $\varphi \in (-\pi, \pi]$ zur positiven reellen Achse, beschrieben
#### Umrechnung von Koordinaten
- Aus $(a, b)$ laesst sich $(r, \varphi)$ folgendermassen ermitteln:
$$r = \sqrt{a^2 + b^2}$$
$$\varphi =
\begin{cases}
arccos(\frac{a}{r}) &\text{, falls $b \geq 0$} \\
-arccos(\frac{a}{r}) &\text{, falls $b < 0$}
\end{cases}
$$
- Umgekehrt gilt:
$$a = cos(\varphi) \cdot r$$
$$b = sin(\varphi) \cdot r$$
$$z = cos(\varphi)r + isin(\varphi)r = r(cos(\varphi) + isin(\varphi))$$
- Letztere Form bezeichnet man als Polardarstellung
#### Arithmetik in Polardarstellung
- Es seien $z_1 = r_1(cos(\varphi_1) + isin(\varphi_1))$ und $z_2 = r_2(cos(\varphi_2) + isin(\varphi_2))$ zwei komplexe Zahlen
###### Multiplikation
$$z_1 \cdot z_2 = r_1r_2(cos(\varphi_1 + \varphi_2) + isin(\varphi_1 + \varphi_2))$$
- Um das Produkt zu bilden, werden somit die Laengen der Zahlen multipliziert und ihre Argumente addiert
###### Potenz
$$z^n = r^n(cos(n\varphi) + isin(n\varphi))$$
###### Wurzel
- Fuer jede komplexe Zahl $z$ und jedes $n \in \mathbb{N}$ sind $z_k$ mit $k \in \{0, 1, ..., n-1\}$ genau die $n$-ten Wurzeln von $z$
- Fuer in $z_k$ gilt:
$$z_k = \sqrt[n]{r}(cos(\frac{\varphi + 2k\pi}{n}) + isin(\frac{\varphi + 2k\pi}{n}))$$