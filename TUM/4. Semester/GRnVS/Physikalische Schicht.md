## Signale
- Mithilfe von Signalen koennen Symbole uebertragen werden, welche Informationen repraesentieren
#### Informationsgehalt
- Der Informationsgehalt $I$ eines Zeiches $x$ haengt von der Wahrschenlichkeit $p(x)$ ab, dass das Zeichen uebertragen wird und wird in bit angegeben:
$$I(x) = -\log_2(p(x))$$
- Der Informationsgehalt eines Zeichens ist somit groesser, je unsicherer dessen Auftritt hervorgesagt werden kann
#### Entropie
- Die Entropie einer Zufallsvariable $X$, die eine Signalquelle emittiert, berechnet sich aus dem Informationsgehalt aller moeglichen Zeichen:
$$H(X) = \sum_{x \in X} p(x) I(x)$$
- Die Entropie gibt hierbei an, wieviele bit benoetigt werden, um ein Zeichen der Signalquelle zu kodieren
###### Bedingte Entropie
- Mithilfe der bedingten Entropie kann ausgedrueckt werden, ob sich die Entropie einer Zufallszahl $Y$ veraendert, falls die Zufallsvariable $X$ bekannt ist:
$$H(Y|X) = \sum_{x \in X} p(x) H(Y|X = x) = \sum_{x \in X} p(x) \sum_{y \in Y} p(y|x) I(y|x)$$
- Ist $H(Y|X) = H(Y)$, so sind die beiden Zufallsvariablen unabhaengig voneinander, andernfalls sind sie voneinander abhaengig
## Signalinterpretation
- Natuerliche Signale sind zeit- und wertkontinuierlich und somit schwer, im ganzen zu erfassen
- Stattdessen werden diese kontinuierlichen Werte diskretisiert
#### Abtasten
- Es wird eine Funktion $\hat{s}(t)$ definiert, welche das urspruengliche Signal $s(t)$ in aequidistanten Abstaenden $T_a$ erfasst:
$$\hat{s}(t) = s(t) \sum_{n = - \infty}^{\infty} \delta[t - nT_a], \space  \text{mit} \space \delta[t - nT_a] = \begin{cases}
1, \space \text{falls} \space t = nT_a \\
0, \space \text{sonst} \\
\end{cases}$$
- Anhand der hierdurch entstehenden Stuetzstellen, kann das urspruengliche Signal mithilfe einer [[Interpolation]] rekonstruiert werden
###### Beispiel
![[Pasted image 20240416151100.png]]
![[Pasted image 20240416151114.png]]