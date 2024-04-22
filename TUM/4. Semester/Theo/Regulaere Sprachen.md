## Deterministische Endliche Automaten 
- Ein DFA kann mithilfe einer Reihe von Zustaenden alle Woerter einer rechtslinearen Sprache repraesentieren
- Mithilfe eines DFAs kann somit das [[Grundlagen formaler Sprache|Wortproblem]] fuer eine rechtslineare Sprache geloest werden
#### Aufbau
- Ein DFA besteht aus:
	- Einer endlichen Zustandsmenge $Q$
	- Einem Eingabealphabet $\Sigma$
	- Eine Uebergangsfunktion $\delta: Q \times \Sigma \rightarrow Q$
	- Einem Startzustand $q_0 \in Q$
	- Einer Menge von Endzustaenden $F \subseteq Q$
#### Worterkennung
- Die von einem DFA akzeptierte Sprache wird beschrieben durch: 
$$L(M) = \left \{ w \in \Sigma^{\star} \mid \hat{\delta}(q_0, w) \in F \right \}$$
- $\hat{\delta}$ wird hierbei rekursiv definiert durch:
$$\hat{\delta}(q, \epsilon) = q$$
$$\hat{\delta}(q, aw) = \hat{\delta}(\delta(q, a), w)$$
- Jeder Buchstabe eines Worts bewirkt somit einen Zustandswechsel im DFA
- Ist der DFA in einem der Endzustaende, sobald das Wort abgearbeitet wurde, so ist es in der repraesentierten Sprache enthalten
## Nichtdeterministische Endliche Automaten
- NFAs sind eine Verallgemeinerung von DFAs und erlauben beliebig viele Zustanduebergaenge fuer jeden Zustand
- Eingaben koennen somit zu unterschiedlichen Zustandsfolgen fuehren
- Ein Wort wird akzeptiert, falls einer der Zustandsfolgen zu einem Endzustand fuehrt
#### Aufbau
- Der Aufbau eines NFA unterscheidet sich von dem eines DFA in der Uebergangsfunktion $\delta: Q \times \Sigma \rightarrow P(Q)$
#### Worterkennung
- Die von einem NFA akzeptierte Sprache aendert sich entsprechend:
$$L(N) = \left \{ w \in \Sigma^{\star} \mid \hat{\bar{\delta}}(\{q_0\}, w) \cap F \neq \emptyset \right \}$$
- Hierfuer wird eine erweiterte Uebergangsfunktion $\bar{\delta}: P(Q) \times \Sigma \rightarrow P(Q)$ definiert:
$$\bar{\delta(S, a)} = \bigcup_{q \in S} \delta(q, a)$$
- $\hat{\bar{\delta}}: P(Q) \times \Sigma^{\star} \rightarrow P(Q)$ ist die Kombination aus $\hat{\delta}$ und $\bar{\delta}$
#### Gemeinsamkeiten mit DFAs
- Jeder NFA kann auch durch einen DFA repraesentiert werden
- Ein Zustand des DFAs entspricht hierbei immer der Menge aller Zustaende, die der NFA mit den bisherigen Eingabebuchstaben annehmen kann
- Die formale Definition eines solchen DFAs ist somit $\left(P(Q), \Sigma, \bar{\delta}, {q_0}, F_M \right)$, mit $F_M = \left \{S \subseteq Q \mid S \cap F \neq \emptyset \right \}$
###### Beispiel
- TODO