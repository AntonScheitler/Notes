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
- Stattdessen werden bei einem digitalen Signal diese kontinuierlichen Werte diskretisiert
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
#### Quantisieren
- Die abgetasteten Werte sind kontinuierlich und koennen nicht exakt abgespeichert werden
- Stattdessen werden Stufen kodiert, auf die die Teile eines Signals dann abgebildet werden
- Das Signal wird somit wertdiskretisiert
###### Beispiel
![[Pasted image 20240422103331.png]]
## Uebertragungskanaele
- Signale werden ueber einen Kanal uebertragen
- Dieser Kanal daempft jedoch eingehende Signale und verzerrt sie durch Rauschen
#### Kanalkapazitaet
- Die maximale Kanalkapazitaet wird durch die Bandbreite $B$ und die Anzahl der unterscheidbaren Signalstufen $M$ eines Kanals festgelegt:
$$C_H = 2B \log_2(M)$$
- Das Rauschen im Kanal verhindert jedoch das beliebige Hinzufuegen von Signalstufen, da diese sonst kaum unterscheidbar waeren
- Das Signal-To-Noise Ration beschreibt wie sehr sich das Kanalrauschen auf ein Signal auswirkt:
$$SNR = \frac{\text{Signalleistung}}{\text{Rauschleistung}} = \frac{P_S}{P_N}$$
- Die Kanalkapazitaet lautet somit:
$$C_s = B \log_2 \left (1 + \frac{P_S}{P_N} \right )$$
## Nachrichtenuebertragung
- Fuer die Uebertragung von Nachrichten muessen unterschiedliche Kodierungsphasen durchlaufen werden
#### Quellenkodierung
- Bei der Quellenkodierung werden Nachrichten durch das Entfernen von Redundanzen komprimiert, um die Effizienz der Uebertragung zu erhoehen
