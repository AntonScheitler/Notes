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
$$A = \left \{ w \in \Omega \mid X(w) = x_i \right \} = A^{-1}(x_i)$$
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
$$Var[X] = \mathbb{E}[X^2] - \mathbb{E}[X^2]$$
$$Var[a \cdot X + b] = a^2 \cdot Var[X]$$