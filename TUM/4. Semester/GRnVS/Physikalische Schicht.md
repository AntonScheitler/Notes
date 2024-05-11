## Signale
- Mithilfe von Signalen koennen Symbole uebertragen werden, welche Informationen repraesentieren
#### Informationsgehalt
- Der Informationsgehalt $I$ eines Zeiches $x$ haengt von der Wahrschenlichkeit $p(x)$ ab, dass das Zeichen uebertragen wird und wird in bit angegeben:
$$I(x) = -\log_2(p(x))$$
- Der Informationsgehalt eines Zeichens ist somit groesser, je unsicherer dessen Auftritt hervorgesagt werden kann
#### Entropie
- Die Entropie einer Zufallsvariable $X$, die eine Signalquelle emittiert, berechnet sich aus dem Informationsgehalt aller moeglichen Zeichen:
$$H(X) = \sum_{x \in X} p(x) I(x)$$
- Die Entropie ist ein Mass der Unvorhersehbarkeit einer Signalquelle und gibt an, wieviele Bit benoetigt werden, um ein Zeichen der Signalquelle zu kodieren
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
- Das Signal wird somit zeitdiskretisiert
- Anhand der hierdurch entstehenden Stuetzstellen, kann das urspruengliche Signal mithilfe einer [[Interpolation]] rekonstruiert werden
###### Beispiel
![[Pasted image 20240416151100.png]]
![[Pasted image 20240416151114.png]]
#### Quantisieren
- Die abgetasteten Werte sind kontinuierlich und koennen nicht exakt abgespeichert werden
- Stattdessen werden Stufen kodiert, auf die die Teile eines Signals dann abgebildet werden
- Das Signal wird somit wertdiskretisiert
###### Quantisierungsfehler
- Liegen die Amplituden eines Signals zwischen $a$ und $b$ und wird mit einer Schrittweite von $\Delta$ quantisiert, so lauten die Quantisierungsstufen $Q = \{ a + \frac{\Delta}{2}, a + \frac{\Delta}{2} + \Delta, ..., b - \frac{\Delta}{2} \}$
- Insbesondere setzen die Quantisierungsstufen nicht direkt bei $a$ und $b$ an
- Der durch, das Quantisieren entstehende Rundungsfehler, ist der Quantisierungsfehler $q_e = \frac{\Delta}{2}$
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
- Binaersequenzen werden hierbei in Codewoerter umgewandelt
#### Kanalkodierung
- Bei der Nachrichtenuebertragung durch einen Kanal kommt es mit hohen Wahrscheinlichkeiten zu Bitfehlern
- Um Bitfehler zu erkennen und zu korrigieren, wird Nachrichten, Redundanz zugefuegt
- Diese Redundanz besteht meist aus Pruefsummen oder Wiederholungen
###### Kodierung
- Codewoerter werden in Bloecke der Laenge $k$ unterteilt und in Kanalwoerter der Laenge $n > k$ kodiert
- Das Verhaeltnis $\frac{k}{n}$ bezeichnet man als Coderate
#### Leitungskodierung
- Durch einen Leitungscode werden Bits, oder Gruppen von Bits, in Grundimpulse kodiert
- Eine Abfolge von Grundimpulsen bildet einen Sendeimpuls
- Je schneller abrupte Signalwechsel erfolgen, desto hoeher muss die Bandbreite des Kanals sein
###### Kodierungsarten
###### Signalisieren des Sendestarts
- Um den Start einer Nachricht zu signalisieren, kann eine Reihe von Bits als Praeambel und Start Frame Delimiter verwendet werden
- Alternativ koennen ueber einen Code, Steuerzeichen erzeugt werden, die dann den Nachrichtenbeginn signalisieren
###### Beispiel
![[Pasted image 20240424181002.png]]
![[Pasted image 20240424181017.png]]
#### Modulation
