## Deterministische Endliche Automaten 
- Ein DFA kann mithilfe einer Reihe von Zustaenden alle Woerter einer rechtslinearen Sprache repraesentieren
- Mithilfe eines DFAs kann somit das Wortproblem fuer eine rechtslineare Sprache geloest werden
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
#### $\epsilon$-NFAs
- Ein $\epsilon$-NFA ist ein NFA mit $\epsilon$-Uebergaengen
- Diese Uebergaenge koennen ohne Eingabebuchstaben traversiert werden
- Fuer jeden $\epsilon$-NFA $N$ gibt es einen NFA $N'$, mit $L(N) = L(N')$
###### Zusammenhang mit NFAs
- Fuer jeden $\epsilon$-NFA $N_{\epsilon}$, gibt es einen NFA $N$ mit $L(N_{\epsilon}) = L(N)$
## Regulaere Ausdruecke
- Regulaere Ausdruecke sind eine alternative Notation fuer rechtslineare Sprachen
- Sie sind somit genauso maechtig, wie DFAs oder NFAs 
#### Aufbau
- Regulaere Ausdruecke werden mithilfe von gewissen Basisausdruecken induktiv definiert
- Diese Basisausdruecke sind $\emptyset$, $\epsilon$, sowie jedes $a \in \Sigma$ und sind selbst regulaere Ausdruecke
- Zwei regulaere Ausdruecke $\alpha$ und $\beta$ koennen kombiniert werden durch $\alpha\beta$, $\alpha | \beta$, oder $\alpha^{\star}$
## Umwandlungen
- DFAs, NFAs, sowie regulaere Ausdruecke koennen ineinander umgewandelt werden
#### Potenzmengenkonstruktion
- Durch die Potenzmengenkonstruktion kann ein NFA in einen DFA umgewandelt werden
###### Vorgehen
- Die Zustaende des DFAs entsprechen der Menge der Zustaende, die ein NFA mit denselben Eingabebuchstaben erreichen kann
- Jeder Zustand ist ein Endzustand, falls er mindestens einen der Endzustand des NFAs enthaelt
###### Tupeldarstellung
- Ist $N = (Q, \Sigma, \delta, q_0, F)$ ein NFA, so kann der DFA, der durch die Potenzmengenkonstruktion erzeugt wird beschrieben werden durch:
$$M = (P(Q), \Sigma, \bar{\delta}, \{q_0\}, F_M), \; \; F_M = (S \subseteq Q \mid S \cap F \neq \emptyset)$$
#### NFAs mit RE-Uebergaengen
- Ein NFA mit RE-Uebergaengen, besitzt Transitionen, die durch regulaere Ausdruecke beschrieben werden
- Hierueber kann ein NFA in einen regulaeren Ausdruck umgewandelt werden und umgekehrt 
###### RE zu $\epsilon$-NFA
- Im Preprocessing werden Terme vereinfacht, die die leere Menge enthalten
- Die Konkatenationen, Auswahlen und Iterationen eines regulaeren Ausdrucks werden in eine Reihe von Zustaenden und Transitionen uebersetzt
![[Pasted image 20240512172953.png]]
![[Pasted image 20240512173003.png]]
###### NFA zu RE
- Dieselben Operationen, die bei der Umwandlung von regulaeren Ausdrucken zu NFAs verwendet werden, werden nun umgekehrt angewandt
![[Pasted image 20240512173115.png]]
![[Pasted image 20240512173121.png]]
#### Lineare Gleichungssysteme
- Ein NFA kann mithilfe von linearen Gleichungssystemen dargestellt werden
- Die Loesung dieser Gleichungssysteme ist ein regulaerer Ausdruck
###### Ardens Lemma
- Die Grundlage fuer das Loesen dieser Gleichungssysteme ist Ardens Lemma
- Sind $a$, $b$, und $X$ regulaere Ausdruecke, mit $\epsilon \notin L(a)$, so gilt:
$$X = aX|b \; \Longrightarrow \; X = a^*b$$
###### Vorgehen
- Das lineare Gleichungssystem wird anhand der Stellen und Transitionen des NFAs erstellt
- Wann immer moeglich, wird Ardens Lemma verwendet, um Gleichungen zu vereinfachen 
- Durch Einsetzen wird das lineare Gleichungssystem verkleinert, bis nurnoch eine Gleichung, mit dem Startzustand auf der linken Seite, verbleibt
###### Beispiel
![[Pasted image 20240512173746.png]]
![[Pasted image 20240512173806.png]]
![[Pasted image 20240512173823.png]]
#### Produkt-Konstruktion
- Sind $M_1 = (Q_1, \Sigma, \delta_1, s_1, F_1)$ und $M_2 = (Q_2, \Sigma, \delta_2, s_2, F_2)$ zwei DFAs, so kann ein Produkt-Automat, der $L(M_1) \cap L(M_2)$ akzeptiert, definiert werden durch:
$$M = (Q_1 \times Q_2, \Sigma, \delta, (s_1, s_2), F_1 \times F_2)$$
$$\delta((q_1, q_2), a) = \left (\delta_1(q_1, a), \delta_2(q_2, a) \right )$$
- Ein Automat, welcher $L(M_1) \cup L(M_2)$ akzeptiert, besitzt denselben Aufbau, jedoch gilt fuer die Endzustaende nun: $F = F_1 \times Q_2 \cup F_2 \times Q_1$
## Abschlusseigenschaften
- Sind $R$, $R_1$, und $R_2$ regulaere Sprachen, so bilden folgende Ausdruecke ebenfalls regulaere Sprachen:
$$R1R2,\; R_1 \cup R_2,\; R^*,\; \overline{R},\; R_1 \cap R_2,\; R_1 \setminus R_2$$
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
- $w \in L(D)$, falls $w$ vom entsprechenden DFA, NFA, akzeptiert wird
###### Entscheidbarkeit
- Das Wortproblem ist fuer DFAs und NFAs entscheidbar
- Fuer DFAs kann das Wortproblem in linearer Zeit geloest werden, fuer NFAs in quadratischer
#### Leerheitsproblem
- Im Leerheitsproblem muss entschieden werden, ob $L(D) = \emptyset$ ist
- $L(D)$ ist leer, falls im entsprechenden DFA, oder NFA kein Endzustand vom Startzustand $q_0$ erreicht werden kann
###### Entscheidbarkeit
- Das Leerheitsproblem ist fuer DFAs und NFAs entscheidbar
- Fuer DFAs kann das Leerheitsproblem in linearer Zeit geloest werden, fuer NFAs in quadratischer
#### Endlichkeitsproblem
- Im Endlichkeitsproblem muss festgestellt werden, ob $|L(D)| = \infty$
- $L(D)$ ist unendlich, falls der entsprechende DFA, oder NFA eine nicht-leere Schleife enthaelt, die zu einem der Endzustaende fuehrt
###### Entscheidbarkeit
- Das Endlichkeitsproblem ist fuer DFAs und NFAs entscheidbar
#### Aequivalenzproblem
- Im Aequivalenzproblem muss bestimmt werden, ob $L_1 = L_2$ ist
- Hierfuer muss folgendes gezeigt werden:
$$L_1 \subseteq L_2 \Leftrightarrow L_1 \cap \overline{L_2} = \emptyset$$
$$L_1 = L_2 \Leftrightarrow (L_1 \subseteq L_2) \land (L_2 \subseteq L_1) $$
###### Entscheidbarkeit
- Das Aequivalenzproblem ist nur fuer DFAs und NFAs entscheidbar
- Fuer DFAs kann das Aequivalenzproblem in quadratischer Zeit geloest werden, fuer NFAs in exponentieller
## Minimierung endlicher Automaten
- Jede regulaere Sprache besitzt einen minimalen Recognizer
- Ein minimierter Automat wird als Quotientenautomat bezeichnet
- Bei DFAs ist ein minimaler Automat stets eindeutig, bei NFAs jedoch nicht
#### Algorithmus
- Alle, nicht erreichbaren Zustaende werden eliminiert
- Alle aequivalenten Zustaende werden bestimmt und zusammengefasst 
- Jede Transition zwischen Zustaenden wird in der Zusammenfassung uebernommen
###### Aequivalente Zustaende
- Zwei Zustaende $p, q$ sind aequivalent, falls fuer alle Woerter $w \in \Sigma^{\star}$ gilt:
$$\hat{\delta}(p, w) \in F \; \Leftrightarrow \; \hat{\delta}(p, w) \in F$$
- Andernfalls sind $p, q$ unterscheidbar
- Somit sind $p \in F$ und $q \notin F$ stets unterscheidbar
- Sind $\delta(p, a)$ und $\delta(q, a)$ in einem DFA unterscheidbar, so sind $p$ und $q$ ebenfalls unterscheidbar
- Unterscheidbarkeit pflanzt sich somit ruecktwaerts fort
###### Implementierung
- Eine Tabelle von umarkierten Paaren $p, q$ wird angelegt
- Jedes Paar mit $p \in F$ und $q \notin F$ wird markiert
- Nun wird jedes Paar $p, q$ markiert, fuer das ein $a \in \Sigma$ existiert, sodass $\{ \delta(p, a), \delta(q, a)\}$ bereits markiert ist
- Wurden alle unmarkierten Paare traversiert, ohne, dass eines markiert wurde, so terminiert der Algorithmus
###### Residualsprachen
- Eine Residualsprache von $L$ bezueglich $w \in \Sigma^*$ wird definiert durch:
$$L^w = \{ z \in \Sigma^* \mid wz \in L  \}$$
- Eine Sprache ist genau dann regulaer, wenn sie endlich viele Residualsprachen hat
###### Effizienz
- Der effizienteste Algorithmus zur Minimierung von Automaten laeuft in $n \log(n)$