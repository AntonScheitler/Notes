## Kontextfreie Grammatiken
- Die Produktionen einer kontextfreien Grammatik enthalten auf der linken Seite nur ein Nichtterminal, wobei es fuer die rechte Seite keine Beschraenkung gibt
#### Ableitungsrelation
- Mithilfe der Albeitungsrelationen, werden ueber die Produktionen Woerter generiert
- Ableitungsrelationen haben die Form $\alpha \rightarrow_G^{n + 1} \gamma$, $\alpha \rightarrow_G^{\star} \gamma$, oder $\alpha \rightarrow_G^{+} \gamma$, falls $\gamma$ durch $\alpha$ in $n + 1$, beliebig vielen, oder mindestens einer Ableitung erreicht werden kann
- Eine Reihe von Ableitungen ist eine Linksableitung, falls stets die linkesten Nichtterminale zuerst abgeleitet werden
#### Syntaxbaeume 
- Da es auf der linken Seite einer Produktion nur ein Nichtterminal gibt, kann ein Syntaxbaum erzeugt werden, wobei innere Knoten durch Nichtterminale und Blaetter durch Terminale repraesentiert werden
- Eltern-Kind Beziehungen werden hierbei durch Produktionen festgelegt
- Der Rand beschreibt das Wort, dass die Blaetter ergeben, wenn sie von links nach rechts gelesen werden
###### Mehrdeutigkeit
- Gibt es fuer ein Wort mehrere, unterschiedliche Syntaxbaeume, die dieses Wort produzieren, so ist die entsprechende Grammatik mehrdeutig 
- Ist jede Grammatik einer Sprache mehrdeutig, so ist die Sprache inhaerent mehrdeutig
###### Beispiel
![[Pasted image 20240525095154.png]]
#### Maechtigkeit
- Um zu Beweisen, dass die Sprache aus einer kontextfreien Grammatik $L(G)$ genauso maechtig ist, wie eine gegebene Sprache $L$, kann Induktion verwendet werden
- Um $L(G) \subseteq L$ zu zeigen, kann eine Induktion ueber die Laenge der Produktionen genutzt werden 
- Um $L \subseteq L(G)$ zu zeigen, wird eine Induktion ueber die Wortlaenge verwendet
## Chomsky Normalform
- Eine Grammatik ist in Chomsky Normalform, falls alle Produktionen eine der folgenden Formen haben:
$$A \rightarrow a \; \; \; \; A \rightarrow BC$$
- Jede Grammatik $G$ kann in ihre Chomsky Normalform $G'$ gebracht werden, sodass $L(G')  = L(G) \setminus \{\epsilon\}$
- $G$ und $G'$ sind somit fast aequivalent
- Der Syntaxbaum, der fuer ein Wort aus einer kontextfreien Grammatik in Chomsky Normalform gewonnen wird, ist binaer
#### Umwandlung
- Die Umwandlung einer kontextfreien Grammatik in eine Grammatik in Chomsky Normalform erfolgt ueber mehrere Schritte
###### Substituieren der Terminale
- Jedes Terminal einer Produktion, deren rechte Seite laenger als $2$ ist, wird durch ein neues Nichtterminal substituiert
- Eine neue Produktion wird eingefuegt, sodass dieses neue Nichtterminal auf das entsprechende Terminal abgeleitet werden kann
###### Substituieren der Nichtterminale
- Die letzten $n-1$ Nichtterminale einer Produktion der Laenge $n \geq 3$ werden durch ein neues Nichtterminal substituiert
- Eine neue Produktion wird eingefuegt, sodass dieses neue Nichtterminal auf die entsprechenden Nichtterminale abgebildet werden kann
###### Eliminieren der $\epsilon$-Produktionen
- Eine Menge $\hat{P}$ wird erstellt, die zunaechst alle Produktionen aus $P$ enthaelt
- Sind $B \rightarrow \epsilon$, sowie $A \rightarrow \alpha B \beta$ in $\hat{P}$ enthalten, so wird auch $A \rightarrow \alpha \beta$ in $\hat{P}$ hinzugefuegt
- Dies wird wiederholt, bis keine neuen Produktionen mehr in $\hat{P}$ eingefuegt werden koennen
- Nun werden alle $\epsilon$-Produktionen aus $\hat{P}$ entfernt, um $G'$ zu erzeugen
###### Eliminieren der Kettenproduktionen
- Eine Menge $\hat{P}$ wird erstellt, die zunaechst alle Produktionen aus $P$ enthaelt
- Sind $A \rightarrow B$, sowie $B \rightarrow a$ in $\hat{P}$ enthalten, so wird auch $A \rightarrow a$ in $\hat{P}$ hinzugefuegt
- Nun werden alle Kettenproduktionen $A \rightarrow B$ aus $\hat{P}$ entfernt, um $G'$ zu erzeugen
## Pumping Lemma
- Fuer jede kontextfreie Sprache $L$ gibt es ein $n \geq 1$, sodass es fuer jedes $z \in L$ mit $|z| \geq n$ eine Zerlegung $uvwxy$ gibt, sodass gilt:
	- $vx \neq \epsilon$
	- $|vwx| \leq n$
	- $\forall i \in \mathbb{N}: uv^iwx^iy \in L$
## Abschlusseigenschaften
- Sind $G_1$ und $G_2$ kontextfreie Grammatiken, so sind die folgenden Sprachen ebenfalls kontextfrei:
	- $L(G_1) \cup L(G_2)$
	- $L(G_1)  L(G_2)$
	- $L(G_1)^*$
	- $L(G_1)^R$
## Algorithmen
- Symbole $X \in V \cup \Sigma$ werden unterschiedlich klassifiziert:
	- $X$ ist nuetzlich, falls es eine Reihe von Ableitungen $S \rightarrow^* w$ gibt, in der $X$ vorkommt
	- $X$ ist erzeugend, falls es eine Reihe von Ableitungen $X \rightarrow^* w$ gibt
	- $X$ ist erreichbar, falls es eine Reihe von Ableitungen $S \rightarrow^* \alpha X \beta$ gibt
- Falls $X$ nuetzlich ist, so ist es auch erzeugend und erreichbar, aber nicht umgekehrt
#### Entfernen unnuetzer Symbole
- Unnuetze Symbole koennen aus einer Grammatik entfernt werden, indem folgende Schritte befolgt werden:
	- Alle nicht erzeugenden Symbole werden entfernt
	- Alle nicht erreichbaren Symbole werden entfernt
#### Cocke-Younger-Kasami Algorithmus
- Mithilfe des CYK Algorithmus kann das Wortproblem fuer kontextfreie Grammatiken in Chomsky Normalform entschieden werden 
- Hierfuer werden die Produktionen $V_{i, j}$ betrachtet, die bestimmte Teilwoerter des Wortes generieren:
$$V_{i, j} = \{ A \in V \mid A \rightarrow_G^* a_i, ..., a_j)$$
###### Vorgehen
- Die $V_{i, j}$ werden rekursiv nach wachsendem $j - i$ berechnet, angefangen bei $V_{ii} = \{ A \in V \mid (A \to a_i) \in P\}$
- Die Groesse der Teilwoerter wird in jedem Schritt um $1$ erhoeht
- In einem Feld $ij$ einer Tabelle werden alle Mengen von Nichtterminalen notiert, welche das Teilwort $a_i, ..., a_j$ erzeugen koennen
- Enthaelt das oberste Feld der Tabelle das Nichtterminal $S$, so kann das Wort von der Grammatik erzeugt werden 
###### Beispiel
![[Pasted image 20240603144116.png]]
## Kellerautomaten
- Mithilfe von Kellerautomaten kann das Wortproblem fuer kontextfreie Sprachen geloest werden
- Der Kellerautomat besteht hierbei aus einem Stack und einem Kontrollgraphen, der das Verhalten des Stacks fuer eingelesene Zeichen festlegt
- Der Kontrollgraph verhaelt sich nicht deterministisch
#### Aufbau
- Ein Kellerautomat $M$ besteht aus:
	- Einer endlichen Zustandsmenge $Q$
	- Einem Eingabealphabet $\Sigma$
	- Einem Kelleralphabet $\Gamma$
	- Einem Anfangszustand $q_0$
	- Dem untersten Kellerzeichen $Z_0$
	- Einer Uebergangsfunktion $\delta: Q \times (\Sigma \cup \{\epsilon\}) \times \Gamma \to P(Q \times \Gamma^*)$
	- Einer Menge von Endzustaenden $F \subseteq Q$
#### Konfiguration
- Die Konfiguration eines Kellerautomaten zu einem gegebenen Zeitpunkt kann durch $(q, w, a)$ dargestellt werden
- $q$ entspricht hierbei dem Zustand des Automaten, $w$ dem verbleibenden, einzulesenden Wort und $a$ dem aktuellen Kellerinhalt
#### Zustandsuebergang
- Die Zustandsuebergangsfunktion akzeptiert einen Zustand $q$, ein Eingabezeichen $a$ und das oberste Kellerzeichen $Z$ und lieferet einen neuen Zustand $q'$, sowie ein neues oberstes Kellerzeichen $Z'$
- Dies kann ueber $(q', Z') \in \delta(q, a, Z)$ ausgedrueckt werden
- Hierdurch koennen push und pop Operationen definiert werden, die Zeichen auf den Stack legen, beziehungsweise davon entfernen
- Ausserdem koennen Zeichen gelesen werden, ohne, dass sich der Stack veraendert
#### Akzeptanz von Woertern
- Ein PDA akzeptiert $w \in \Sigma^*$ mit Endzustand, genau dann wenn:
$$(q_0, w, Z_0) \to_{M}^* (f, \epsilon, \gamma), \; \; f \in F, \gamma \in \Gamma$$
- Die Menge der Woerter, die diese Bedingung erfuellen, wird mit $L_F(M)$ beschrieben
- Ein PDA akzeptiert $w \in \Sigma^*$ mit leerem Stack, genau dann wenn:
$$(q_0, w, Z_0) \to_{M}^* (q, \epsilon, \epsilon), \; \; q \in Q$$
- Die Menge der Woerter, die diese Bedingung erfuellen, wird mit $L_{\epsilon}(M)$ beschrieben
#### Grammatik zu PDA
- Eine kontextfreie Grammatik kann folgendermassen in einen PDA umgewandelt werden:
	- Fuer den PDA wird genau ein Zustand angelegt
	- Fuer alle Produktionen $A \to \beta$ wird die Transition $\epsilon, A/\beta$ eingefuegt
	- Fuer alle Terminale $a$ wird die Transition $a, a/\epsilon$ eingefuegt
###### Endzustand zu leerem Keller
- Um einen PDA $M$, der mit Endzustaenden akzeptiert in einen PDA $M'$ umzuwandeln, der mit leerem Keller akzeptiert, werden folgende Schritte ausgefuehrt:
	- Der Startzustand von $M'$ besitzt einen $\epsilon$ Uebergang, der ein Zeichen $Z_0'$ auf den Stack legt und in den Startzustand von $M$ uebergeht
	- Jeder Endzustand von $M$ besitzt einen Uebergang, der alle Zeichen vom Keller entfernt 
###### Leerer Keller zu Endzustand
- Um einen PDA $M$, der mit leerem Keller akzeptiert in einen PDA $M'$ umzuwandeln, der mit Endzustaenden akzeptiert, werden folgende Schritte ausgefuehrt:
	- Der Startzustand von $M'$ besitzt einen $\epsilon$ Uebergang, der ein Zeichen $Z_0'$ auf den Stack legt und in den Startzustand von $M$ uebergeht
	- Aus jedem Zustand kann in einen Endzustand gewechselt werden, falls $Z_0'$ das einzige Zeichen auf dem Stack ist
## Deterministischer Kellerautomat
- Ein Kellerautomat ist deterministisch, falls fuer jede Kombination aus Zustand, eingelesenem Zeichen und obserstem Kellerzeichen hoechstens ein Uebergang definiert ist 
- Gibt es fuer ein Zustand und ein oberstes Kellerzeichen einen $\epsilon$ Uebergang, so darf dies der einzige Uebergang fuer diese Konfiguration sein
- Ein Kellerautomat ist somit deterministisch, falls fuer alle $q \in Q$, $a \in \Sigma$ und $Z \in \Gamma$ gilt:
$$|\delta(q, a, Z)| + |\delta(q, \epsilon, Z)| \leq 1$$
#### Praefix Bedingung
- Eine Sprache erfuellt die Praefix Bedingung, genau dann, wenn sie keine zwei Woerter enthaelt, sodass das eine ein echter Praefix des anderen ist
- Es existiert ein DPDA $M$ fuer $L = L_{\epsilon}(M)$ genau dann, wenn es einen DPDA $M$ fuer $L = L_F(M)$ gibt und $L$ die Praefix Bedingung erfuellt
- Die Akzeptanz ueber Endzustaende ist somit maechtiger als die Akzeptanz ueber den leeren Stack
#### Deterministische Kontextfreie Sprachen
- Die Sprache, die von einem DPDA akzeptiert wird, wird als deterministisch kontextfrei bezeichnet
- Die Klasse der deterministischen kontextfreien Sprachen ist unter dem Komplement abgeschlossen, jedoch nicht unter Vereinigung oder Schnitt
###### Eigenschaften
- DCFL sind nicht inhaerent mehrdeutig
- Das Wortproblem fuer DCFL ist in linearer Zeit loesbar
