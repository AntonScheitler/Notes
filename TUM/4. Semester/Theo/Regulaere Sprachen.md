## Deterministische Endliche Automaten 
- Ein DFA kann mithilfe einer Reihe von Zustaenden alle Woerter einer rechtslinearen Sprache repraesentieren
- Mithilfe eines DFAs kann somit das [[Grundlagen formaler Sprache|Wortproblem]] fuer eine rechtslineare Sprache geloest werden
#### Aufbau
- Ein DFA besteht aus:
	- Einer endlichen Zustandsmenge $Q$
	- Einem Eingabealphabet $\Sigma$
	- Einer Uebergangsfunktion $\delta: Q \times \Sigma \rightarrow Q$
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
#### Umwandlung zu DFAs
- Jeder NFA kann auch durch einen DFA repraesentiert werden
- Ein Zustand des DFAs entspricht hierbei immer der Menge aller Zustaende, die der NFA mit denselben Eingabebuchstaben annehmen kann
- Die formale Definition eines solchen DFAs ist somit $\left(P(Q), \Sigma, \bar{\delta}, {q_0}, F_M \right)$, mit $F_M = \left \{S \subseteq Q \mid S \cap F \neq \emptyset \right \}$
#### $\epsilon$-NFAs
- Ein $\epsilon$-NFA ist ein NFA mit $\epsilon$-Uebergaengen
- Diese Uebergaenge koennen ohne Eingabebuchstaben traversiert werden
###### Zusammenhang mit NFAs
- Fuer jeden $\epsilon$-NFA $N_{\epsilon}$, gibt es einen NFA $N$ mit $L(N_{\epsilon}) = L(N)$
## Regulaere Ausdruecke
- Regulaere Ausdruecke sind eine alternative Notation fuer rechtslineare Sprachen
- Sie sind somit genauso maechtig, wie DFAs oder NFAs 
#### Aufbau
- Regulaere Ausdruecke werden mithilfe von gewissen Basisausdruecken induktiv definiert
- Diese Basisausdruecke sind $\emptyset$, $\epsilon$, sowie jedes $a \in \Sigma$ und sind selbst regulaere Ausdruecke
- Zwei regulaere Ausdruecke $\alpha$ und $\beta$ koennen kombiniert werden durch $\alpha\beta$, $\alpha | \beta$, oder $\alpha^{\star}$
#### Umwandeln von NFAs 
- Ein beliebiger NFA kann mithilfe einer Reihe von Regeln in einen regulaeren Ausdruck umgewandelt werden
###### Lineare Gleichungssystemen
- Ein lineares Gleichungssystem kann anhand eines NFAs erstellt werden
- Dieses lineare Gleichungssystem kann dann einen regulaeren Ausdruck umgeformt werden
###### Beispiel
![[Pasted image 20240430153859.png]]
![[Pasted image 20240430153959.png]]
## Pumping Lemma
- Um zu bestimmen, ob eine gegebene Sprache regulaer ist, kann das Pumping Lemma verwendet werden
#### Lemma
- Ist $R \subseteq \Sigma$ regulaer, so gibt es ein $n$, sodass fuer alle $z \in R$ mit $|z| \geq n$ mit $z = uvw$ git:
	- $v \neq \epsilon$
	- $|uv| \leq n$
	- $\forall \, i \geq 0: uv^iw \in R$
#### Beweis
- Mithilfe eines Widerspruchsbeweises kann gezeigt werden, dass eine Sprache nicht regulaer ist
- Hierbei werden $n$ und $z \in R$ allgemein gewaehlt und es wird gezeigt, dass es keine Zerlegung $z = uvw$ gibt, die das Pumping Lemma erfuellt
## Entscheidungsprobleme
- Bei einem Entscheidungsproblem muss festgestellt werden, ob eine regulaere Sprache in einem gegebenen Format $D$ eine bestimmte Eigenschaft erfuellt
- Ein Entscheidungsproblem ist entscheidbar, falls fuer jede Eingabe die korrekte Loesung in endlicher Zeit bestimmt werden kann
- Nicht alle Entscheidungsprobleme sind entscheidbar
#### Wortproblem
- Im Wortproblem muss fuer ein Wort $w$ entschieden werden, ob $w \in L(D)$
#### Leerheitsproblem
- Im Leerheitsproblem muss entschieden werden, ob $L(D) = \emptyset$ ist