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
$$\mathbb{E}[X] = \int_{- \infty}^{\infty} t \cdot f_X(t) \; \mathrm{d}t$$
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
$$f(x) = \frac{1}{\sqrt{2 \pi}\sigma} \cdot \exp \left ( - \frac{(x - \mu)^2}{2\sigma^2}\right ) = \varphi(x; \mu, \sigma)$$
$$F(x) = \frac{1}{\sqrt{2 \pi}\sigma} \cdot \int_{- \infty}^x \exp \left ( - \frac{(t - \mu)^2}{2\sigma^2} \right ) \; \mathrm{d}t = \Phi(x, \mu, \sigma)$$
- Falls $\mu = 0$ und $\sigma = 1$, sodass $X \sim \mathcal{N}(0, 1)$, so handelt es sich bei $X$ um eine standardnormalverteilte Zufallsvariable, wobei gilt:
- Fuer eine normalverteilte Zufallsvariable $X \sim \mathcal{N}(\mu, \sigma^2)$ gilt:
$$\mathbb{E}[X] = \mu, \; Var[X] = \sigma^2$$
###### Lineare Transformation
- Ist $X \sim \mathcal{N}(\mu, \sigma^2)$ eine normalverteilte Zufallsvariable, so ist $Y = aX + b$, mit $a \in \mathbb{R} \setminus \{0\}$ und $b \in \mathbb{R}$ ebenfalls normalverteilt mit $Y \sim \mathcal{N}(a \mu + b, a^2\sigma^2)$
#### Exponentialverteilung
- Eine Zufallsvariable $X$ ist exponentialverteilt, mit dem Parameter $\lambda$, falls sie folgende Dichte und Verteilung besitzt: 
$$f_X(x) = \begin{cases}
\lambda \cdot e^{-\lambda x}, \; x \geq 0 \\
0, \; \text{sonst}
\end{cases}$$
$$F_X(x) = \int_0^x \lambda \cdot e^{- \lambda t} \; \mathrm{d}t = 1 - e^{-\lambda x}$$
- Fuer den Erwartungswert und die Varianz gelten zudem:
$$\mathbb{E}[X] = \frac{1}{\lambda}$$
$$Var[X] = \frac{1}{\lambda^2}$$
- Aehnlich zur geometrischen Verteilung ist die Exponentialverteilung ebenfalls gedaechnislos
###### Skalierung exponentialverteilter Zufallsvariablen
- Ist $X$ eine exponentialverteilte Zufallsvariable mit dem Parameter $\lambda$, so ist $Y = aX$, mit $a > 0$ ebenfalls exponentialverteilt mit dem Parameter $\frac{\lambda}{a}$ 
###### Warteprobleme
- Sind die Zufallsvariablen $X_1, ..., X_n$ exponentialverteilt mit den Parametern $\lambda_1, ..., \lambda_n$, so ist auch $X = min(X_1, ..., X_n)$ exponentialverteilt mit dem Parameter $\lambda_1 + ... + \lambda_n$
## Mehrere Zufallsvariablen
- Fuer zwei kontinuierliche Zufallsvariablen wird die gemeinsame Dichte ueber eine integrierbare Dichtefunktion beschrieben, wobei:
$$Pr[A] = \int_A f_{X, Y}(x, y) \; \mathrm{d}x \; \mathrm{d} y$$
$$\int_{- \infty}^{\infty} \int_{- \infty}^{\infty} f_{X, Y}(x, y) \; \mathrm{d} x \; \mathrm{d} y = 1$$
- Fuer die Verteilungsfunktion gilt zudem:
$$F_{X, Y}(x, y) = \int_{- \infty}^{y} \int_{- \infty}^{x} f_{X, Y}(u, v) \; \mathrm{d} u \; \mathrm{d} v$$
#### Randdichte und Randverteilung
- Die Randdichte von $X$ kann anhand der gemeinsamen Dichtefunktion beschrieben werden: 
$$f_X(x) = \int_{-\infty}^{\infty} f_{X, Y}(x, v) \; \mathrm{d} v$$
- Fuer die Randverteilung von $X$ gilt somit:
$$F_X(x) = \int_{- \infty}^x \left [\int_{-\infty}^{\infty} f_{X, Y}(u, v) \; \mathrm{d} v \right ] \; \mathrm{d} u$$
#### Unabhaengigkeit
- Zwei Zufallsvariablen $X$ und $Y$ sind unabhaengig, falls gilt:
$$f_{X, Y}(x, y) = f_X(x) \cdot f_Y(y)$$
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