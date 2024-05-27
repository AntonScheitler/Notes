## Allgemeines
- Ein diskreter Wahrscheinlichkeitsraum wird durch eine Menge $\Omega = \{\omega_1, \omega2, ... \}$ von Elementarereignissen und ihren Wahrscheinlichkeiten festgelegt
- Fuer die Wahrscheinlichkeit der Elementarereignisse gilt:
$$\sum_{\omega \in \Omega} Pr[\omega] = 1$$
#### Ereignis
- Ein Ereignis ist eine Menge $E \subseteq \Omega$
- Fuer die Wahrscheinlichkeit $Pr[E]$ eines Ereignisses gilt:
$$Pr[E] = \sum_{\omega \in E} Pr[\omega]$$
###### Siebformel
- Um die Wahrscheinlichkeit der Vereinigung mehrerer Ereignisse zu berechnen, wird die Siebformel verwendet
$$Pr[A \cup B] = Pr[A] + Pr[B] - Pr[A \cap B]$$
- Fuer drei Ereignisse $A, B$ und $C$ gilt insbesondere:
$$Pr[A \cup B \cup C] = Pr[A] + Pr[B] + Pr[C] - Pr[A \cap B] - Pr[A \cap C] - Pr[B \cap C] + Pr [A \cap B \cap C]$$
## Bedingte Wahrscheinlichkeit
- Bei zwei Ereignissen $A$ und $B$ wird die bedingte Wahrscheinlichkeit $Pr[A|B]$ vom Eintreten von $A$, falls $B$ gegeben ist, definiert durch:
$$Pr[A|B] = \frac{Pr[A \cap B]}{Pr[B]}$$
- Somit gilt fuer $Pr[A \cap B]$:
$$Pr[A \cap B] = Pr[A | B] \cdot Pr[B] = Pr[B | A] \cdot Pr[A]$$
#### Satz der totalen Wahrscheinlichkeit
- Sind die Ereignisse $A_1, ..., A_n$ paarweise disjunkt und $B \subseteq A_1 \, \cup \, ... \cup \, A_n$, so gilt:
$$Pr[B] = \sum_{i = 1}^n Pr[B | A_i] \cdot Pr[A_i] = \sum_{i = 1}^n Pr[B \cap A_i]$$
#### Unabhaengigkeit
- Zwei Ereignisse $A$ und $B$ sind unabhaengig, falls gilt:
$$Pr[A \cap B] = Pr[A] \cdot Pr[B]$$
- Sind $A$ und $B$ somit unabhaengig mit $Pr[A], Pr[B] \gt 0$, so koennen sie nicht disjunkt sein, da sonst folgender Widerspruch gilt:
$$Pr[A \cap B] = Pr[\emptyset] = 0 = Pr[A] \cdot Pr[B]$$
- Aus der Unabhaengigkeit von $A$ und $B$ folgt zudem die Unabhaengigkeit ihrer Komplemente
## Zufallsvariablen
- Eine Zufallsvariable $X$ ist eine Abbildung $X: \Omega \rightarrow \mathbb{R}$ und ist diskret, falls $\Omega$ endlich, oder abzaehlbar unendlich ist
- Fuer den Wertebereich $W_X$ von $X$ gilt:
$$W_X = \left \{ x \in \mathbb{R} \mid \exists \, w \in \Omega: X(w) = x \right \}$$
- Ereignisse $A_i$ koennen somit anhand von Bildern $x_i$ von $X$ definiert werden:
$$A_i = \left \{ w \in \Omega \mid X(w) = x_i \right \} = A_i^{-1}(x_i)$$
- Die Wahrscheinlichkeit von $A_i$ kann durch $Pr[X = x_i]$ ausgedrueckt werden
#### Dichte und Verteilung
- Die Dichtefunktion $f_X$, sowie die Verteilungsfunktion $F_X$ werden definiert durch:
$$f_X(x) = Pr[X = x]$$
$$F_X(x) = \sum_{x' \in W_X, \ x' \leq x} Pr[X = x]$$
#### Erwartungswert
- Der Erwartungswert $\mathbb{E}[X]$ wird definiert durch:
$$\mathbb{E}[X] = \sum_{x \in W_X} x \cdot Pr[X = x]$$
- Damit ein Erwartungswert existieren kann, muss somit $\sum_{x \in W_X} x \cdot Pr[X = x]$ konvergieren
- Fuer Umrechnungen gilt:
$$\mathbb{E}[a \cdot X + b] = a \cdot \mathbb{E}[X] + b$$
###### Verknuepfung
- Eine zusaetzliche Funktion kann auf eine Zufallsvariable angewandt werden, um eine neue Zufallsvariable zu erzeugen:
$$Y = f \circ X = f(X)$$
- Fuer den Erwartungswert von $Y$ gilt somit:
$$\mathbb{E}(Y) = \sum_{y \in W_Y} y \cdot Pr[Y = y] = \sum_{y \in W_Y} y \cdot \sum_{x: f(x) = y} Pr[X = x] = \sum_{x \in W_X} f(x) \cdot Pr[X = x]$$
###### Bedingte Zufallsvariablen
- Eine bedingte Zufallsvariable kann durch $X|A$ ausgedrueckt werden
- Hierbei gilt:
$$Pr[X = x | A] = \frac{Pr[X = x \cap A]}{Pr[A]}$$
- Der Satz der totalen Wahrscheinlichkeit kann auf den Erwartungswert bedingter Zufallsvariablen uebertragen werden:
$$\mathbb{E}[X] = \sum_{i = 1}^{n} \mathbb{E}[X | A_i] \cdot Pr[A_i]$$
#### Varianz
- Die Varianz ist die quadratische Abweichung einer Zufallsvariable von ihrem Erwartungswert:
$$Var[X] = \mathbb{E}[(X - \mu)^2] = \sum_{x \in W_X} (x - \mu)^2 \cdot Pr[X = x]$$
- Fuer die Varianz gilt bei Umrechnungen:
$$Var[X] = \mathbb{E}[X^2] - \mathbb{E}[X]^2$$
$$Var[a \cdot X + b] = a^2 \cdot Var[X]$$
#### Indikatorvariable
- Eine Indikatorvariable $I_A$ ist eine Zufallsvariable zu einem Ereignis $A$, fuer die gilt:
$$I_A = \begin{cases}
1, \; \text{falls} \; A \; \text{eintritt} \\
0, \; \text{sonst}
\end{cases}$$
## Mehrere Zufallsvariablen
- In einem Zufallsexperiment ist es moeglich, mehr als eine Zufallsvariable zu definieren
- Die Wahrscheinlichkeit, dass die Zufallsvariablen, beispielsweise $X$ und $Y$, bestimmte Werte annehmen, wird durch $Pr[X = x, Y = y]$, beziehungsweise $Pr[X = x \land Y = y]$ beschrieben
#### Dichte und Verteilung
- Die gemeinsame Dichte zweier Zufallsvariablen $X$ und $Y$ wird definiert durch:
$$f_{X, Y}(x, y) = Pr[X = x, Y = y]$$
- Die gemeinsame Verteilung der Zufallsvariablen wird definiert durch:
$$F_{X, Y}(x, y) = \sum_{x' \leq x} \sum_{y' \leq y} f_{X, Y}(x', y')$$
###### Randdichte
- Aus der gemeinsamen Dichte koennen die Randdichten $f_X$ und $f_Y$ abgeleitet werden:
$$f_X(x) = \sum_{y \in W_Y} f_{X, Y}(x, y)$$
$$f_Y(y) = \sum_{x \in W_X} f_{X, Y}(x, y)$$
- Hierbei gilt zudem:
$$f_X(x) = Pr[X = x], \; f_Y(x) = Pr[Y = y]$$
###### Randverteilung
- Aehnlich zur Randdichte wird auch die Randverteilung definiert:
$$F_X(x) = \sum_{x' \leq x} f_X(x')$$
$$F_Y(y) = \sum_{y' \leq y} f_Y(y')$$
#### Unabhaengigkeit
- Zwei Zufallsvariablen $X$ und $Y$ sind unabhaengig, falls gilt:
$$Pr[X = x, Y = y] = Pr[X = x] \cdot Pr[Y = y]$$
#### Zusammengesetzte Zufallsvariablen
- Neue Zufallsvariablen koennen erstellt werden, indem bestehende Zufallsvariablen, beispielsweise durch Addition zusammengefasst werden
- Fuer eine Zufallsvariable $Z = X + Y$ mit unabhaengigen $X$ und $Y$ gilt hierbei die Faltungsformel:
$$f_Z(z) = \sum_{x \in W_X} f_X(x) \cdot f_Y(z - x)$$
###### Erwartungswert
- Fuer den Erwartungswert der zusammengesetzten Zufallsvariable $X = a_1X_1 + ... + a_nX_n$ gilt:
$$\mathbb{E}[X] = a_1 \mathbb{E}[X_1] + ... + a_n \mathbb{E}[X_n]$$
- Sind $X_1, ..., X_n$ unabhaengig, so gilt zudem:
$$\mathbb{E}[X_1 \cdot \; ... \; \cdot X_n] = \mathbb{E}[X_1] \cdot \; ... \; \cdot \mathbb{E}[X_n]$$
###### Varianz
- Fuer die Varianz von $X = X_1 + ... + X_n$, mit unabhaengigen $X_1, ..., X_n$ gilt:
$$Var[X] = Var[X_1] + ... + Var[X_n]$$
## Diskrete Verteilungen
- Bestimmte Verteilungen erscheinen haeufig in der diskreten Wahrscheinlichkeitstheorie
#### Bernoulli Verteilung
- Eine Zufallsvariable $X$ ist Bernoulli-verteilt, falls ihr Wertebereicht $W_X = \{0, 1\}$ ist, und sie folgende Dichte besitzt:
$$f_X(x) = \begin{cases}
p, \; \text{falls} \; x = 1 \\
1 - p, \; \text{falls} \; x = 0 \\
\end{cases}$$
- $X$ ist somit eine Indikatorvariable
- Fuer den Erwartungswert und die Varianz von $X$ gilt hierbei:
$$\mathbb{E}[X] = p, \; Var[X] = p(1-p)$$
###### Binomial Verteilung
- Betrachtet man Summen von Indikatorvariablen, so wird die Binomialverteilung verwendet
- Ist $X = X_1 + ... + X_n$ eine Summe aus $n$ Indikatorvariablen, welche jeweils die Erfolgswahrscheinlichkeit $p$ besitzten, so ist der Wertebereich $W_X = \{0, ..., n\}$ und fuer die Dichte gilt:
$$f_X(x) = b(x;n,p) = \binom{n}{x}p^x(1 - p)^{n - x}$$
- Der Erwartungswert und die Varianz von $X$ lassen sich aus der Bernoulli Verteilung ableiten:
$$\mathbb{E}[X] = np, \; Var[X] = np(1-p)$$
- Ist $X$ binomialverteilt, so wird dies durch $X \sim Bin(n, p)$ ausgedrueckt
- Sind $X \sim Bin(n_X, p)$ und $Y \sim Bin(n_Y, p)$, so ist folgt fuer $Z = X + Y$, dass $Z \sim Bin(n_X + n_Y, p)$
#### Geometrische Verteilung
- Wird ein Experiment mit Erfolgswahrscheinlichkeit $p$ solange durchgefuehrt, bis ein Erfolg eintritt, so bezeichne die Zufallsvariable $X$ die Anzahl der Versuche, bis ein Erfolg eintritt
- Fuer die Dichte von $X$ gilt hierbei:
$$f_X(i) = p(1-p)^{i - 1}$$
- Der Erwartungswert und die Varianz ergeben sich somit zu:
$$\mathbb{E}[X] = \frac{1}{p}, \; Var[X] = \frac{1 - p}{p^2}$$
###### Negative Binomialverteilung
- Ist $Z = X_1 + ... + X_n$ eine Summe aus $n$ geometrisch verteilten Zufallsvariablen, so bezeichnet sie die Anzahl der Versuche, bis alle $n$ Experimente erfolgreich sind
- Bei $Z = z$ gibt es somit $n$ erfolgreiche und $z - n$ erfolglose Experimente
- Fuer die Dichte von $Z$ gilt somit:
$$f_Z(z) = \binom{z - 1}{n - 1} \cdot p^n(1 - p)^{z - n}$$
- $Z$ ist somit negativ binomialverteilt
#### Poisson Verteilung
- Erfolgt ein Experiment mit einer bestimmten Rate in einem Zeitintervall, mit jeweils unabhaengigen Erfolgen, so kann die Anzahl der Erfolge in einem Zeitintervall durch die Poisson Verteilung ausgedrueckt werden
- Bezeichnet die Zufallsvariable $X$ die Anzahl der Erfolge in einem Zeitintervall, bei einer Rate $\lambda$, so gilt fuert die Dichte:
$$f_X(i) = \frac{e^{-\lambda}\lambda^i}{i!}$$
- Fuer den Erwartungswert und die Varianz gilt somit:
$$\mathbb{E}[X] = \lambda, \; Var[X] = \lambda$$
- Ist $X$ poissonverteilt, so wird dies durch $X \sim Po(\lambda)$ ausgedrueckt
###### Zusammenhang mit der Binomialverteilung
- Die Binomialverteiung einer Zufallsvariable $X$ mit $X \sim Bin(n, \lambda /n)$ naehrt sich fuer $n \to \infty$ an die Poisson Verteilung $Po(\lambda)$ an
###### Summe von Zufallsvariablen
- Sind $X \sim Po(\lambda)$ und $Y \sim Po(\mu)$, so gilt fuer $Z = X + Y$, dass $Z \sim Po(\lambda + \mu)$
## Abschaetzen von Wahrscheinlichkeiten
- Es gibt unterschiedliche Methoden, um Wahrscheinlichkeiten nicht genau zu bestimmen, sondern zu approximieren
#### Markov Ungleichung
- Ist $X$ eine Zufallsvariable, die nur nicht-negative Werte annimmt, dann gilt fuer alle $t \in \mathbb{R^+}$:
$$Pr[X \geq t] \leq \frac{\mathbb{E}[X]}{t}$$
#### Chebyshev Ungleichung
- Ist $X$ eine Zufallsvariable, und $t \in \mathbb{R^+}$, so gilt:
$$Pr[|X - \mathbb{E}[X]| \geq t] \leq \frac{Var[X]}{t^2}$$
#### Gesetz der grossen Zahlen
- Es sei $X$ eine Zufallsvariable mit beliebigen, aber festen $\varepsilon, \delta > 0$, und mit $n \geq \frac{Var[X]}{\varepsilon \delta^2}$
- Sind $X_1, ..., X_n$ unabhaengige Zufallszahlen mit derselben Verteilung wie $X$ und ist $Z = \frac{X_1 + ... + X_n}{n}$, so gilt:
$$Pr[|Z - \mathbb{E}[X]| \geq \delta] \leq \varepsilon$$