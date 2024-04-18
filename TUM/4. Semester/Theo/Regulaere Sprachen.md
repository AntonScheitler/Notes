## Deterministische Endliche Automaten 
- Ein DFA kann mithilfe einer Reihe von Zustaenden alle Woerter einer regulaeren Sprache repraesentieren
- Mithilfe eines DFAs kann somit das [[Grundlagen formaler Sprache|Wortproblem]] fuer eine regulaere Sprache geloest werden
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