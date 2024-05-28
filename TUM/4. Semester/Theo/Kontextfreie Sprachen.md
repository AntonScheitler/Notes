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