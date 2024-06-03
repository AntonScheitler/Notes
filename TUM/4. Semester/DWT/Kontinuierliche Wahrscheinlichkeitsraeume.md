## Kontinuierliche Zufallsvariablen
- Eine kontinuierliche Zufallsvariable $X$ besitzt eine integrierbare Dichtefunktion:
$$\int_{- \infty}^{\infty} f_X(x) \; \mathrm{d} x = 1$$
- Die Verteilungsfunktion von $X$ wird somit anhand von Integration definiert:
$$F_X(x) = \int_{- \infty}^x f_X(t) \; \mathrm{d} t$$
#### Ereignisse
- Ein Ereignis $A$ wird durch die Vereinigung paarweise disjunkter Intervalle $I_k$ definiert
- Die Wahrscheinlichkeit, eines Ereignisses kann somit ausgedrueckt werden durch: 
$$Pr[A] = \sum_{k} \int_{I_k} f_X(x) \; \mathrm{d}x$$
#### Eigenschaften der Verteilungsfunktion
- Aufgrund der Definition der Verteilung gilt:
$$Pr[a < X \leq b] = F_X(b) - F_X(a)$$
- Insbesondere besitzen die Ereignisse $a < X < b$, $a \leq X < b$, $a < X \leq b$, $a \leq X \leq b$ dieselbe Wahrscheinlichkeit
#### Funktionen von Zufallsvariablen
- Ist $Y = g(X)$, $g: \mathbb{R} \to \mathbb{R}$, so gilt fuer die Verteilung von $Y$:
$$F_Y(y) = Pr[Y \leq y] = Pr[g(X) \leq y] = \int_C f_X(t) \; \mathrm{d}t$$
- Hierbei gilt $C = \{t \in \mathbb{R} \mid g(t) \leq y\}$ 
- Die Dichtefunktion kann zudem durch Ableiten von $F_Y(y)$ bestimmt werden
#### Erwartungswert und Varianz
- Der Erwartungswert einer kontinuierlichen Zufallsvariable $X$ wird definiert ueber: 
$$\mathbb{E}[X] = \int_{- \infty}^{\infty} t \cdot f_X(t) \; \mathrm{d}x$$
- Fuer die Varianz gilt dementspreched:
$$Var[X] = \mathbb{E}[X^2] - \mathbb{E}[X]^2 = \int_{- \infty}^{\infty} (t - \mathbb{E}[X])^2 \cdot f_X(t) \; \mathrm{d}t$$
## Stetige Verteilungen
- In kontinuierlichen Wahrscheinlichkeitsraeumen unterscheidet man verschiedene Verteilungen
#### Gleichverteilung
- Fuer die Dichte und Verteilung einer gleichverteilten Zufallsvariable $X$ gilt:
$$f_X(x) = \begin{cases}
\frac{1}{b - a}, \; x \in [a, b] \\
0, \; \text{sonst} \\
\end{cases}$$
$$F_X(x) = \begin{cases}
0, \; x < a \\
\frac{x - a}{b - a}, \; a \leq x \leq b \\
1, \; x > b \\
\end{cases}$$
- Fuer den Erwartungswert und die Varianz gelten:
$$\mathbb{E}[X] = \frac{a + b}{2}$$
$$Var[X] = \frac{(a + b)^2}{12}$$
#### Normalverteilung
- Eine Zufallsvariable $X$ ist normalverteilt mit den Parametern $\mu \in \mathbb{R}$ und $\sigma \in \mathbb{R}^+$, falls sie die folgende Dichte und Verteilung besitzt:
$$f(x) = \frac{1}{\sqrt{2 \pi}\sigma} \cdot \exp \left ( - \frac{(x - \mu)^2}{2\sigma^s}\right ) = \varphi(x; \mu, \sigma)$$
$$F(x) = \frac{1}{\sqrt{2 \pi}\sigma} \cdot \int_{- \infty}^x \exp \left ( - \frac{(t - \mu)^2}{2\sigma^2} \right ) \; \mathrm{d}t = \Phi(x, \mu, \sigma)$$
- Falls $\mu = 0$ und $\sigma = 1$, so handelt es sich bei $X$ um eine standardnormalverteilte Zufallsvariable mit der Dichte $\varphi(x)$
## $\sigma$ Algebren
- Eine Menge $\mathbb{A} \subseteq P(\Omega)$ heisst $\sigma$ Algebra, falls folgende Bedingungen erfuellt sind: 
	- $\Omega \in \mathbb{A}$
	- $A \in \mathbb{A} \Longrightarrow \bar{A} \in \mathbb{A}$
	- $A_n \in \mathbb{A} \Longrightarrow \bigcup_{n = 1}^{\infty} A_n \in \mathbb{A}$
#### Wahrscheinlichkeitsraum
- Es sei $\Omega$ eine beliebige Menge und $\mathbb{A}$ eine $\sigma$ Algebra ueber $\Omega$
- Eine Abbildung $Pr[]: \mathbb{A} \to [0, 1]$ hiesst Wahrscheinlichkeitsmass, falls gilt:
	- $Pr[\Omega] = 1$
	- Sind $A_1, A_2, ...$ paarweise disjunkt, so gilt $Pr \left [ \bigcup_{i = 1}^{\infty} A_i \right ] = \sum_{i = 1}^{\infty} Pr[A_j]$
- Ein Wahrscheinlichkeitsraum wird durch das Tupel $(\Omega, \mathbb{A}, Pr)$ definiert