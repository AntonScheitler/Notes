## Definitionen
- Ein Alphabet $\Sigma$ ist eine endliche Menge an Elementen
#### Woerter
- Woerter sind Folgen von Zeichen aus einem Alphabet $\Sigma$
- Jedes Alphabet besitzt das leere Wort $\epsilon$ der Laenge $0$
- Beliebige Woerter $u$ und $v$ koennen durch $uv$, oder $u^3 = uuu$ konkateniert werden
#### Sprache
- $\Sigma^{\star}$ ist die Menge aller moeglichen Woerter ueber $\Sigma$, wobei $\Sigma^{+}$ die Menge aller nicht-leeren Woerter ist
- Eine Teilmenge $L \subseteq \Sigma^{\star}$ ist eine formale Sprache
## Operationen
- Auf Sprachen koennen Operationen angewandt werden
#### Regeln
- Fuer Sprachoperationen gelten unterschiedliche Regeln:
	$\emptyset A = \emptyset$
	$\{\epsilon\} A = A$
	$A(B \cup C) = AB \cup AC$
	$(A \cup B)C = AC \cup BC$
	$A^{\star}A^{\star} = A^{\star}$
## Grammatik
- Die Grammatik einer Sprache legt ihr verhalten fest und wird als $4$-Tupel $G = (V, \Sigma, P, S)$ definiert
#### Aufbau
- $V$ ist eine Menge von Nichtterminalen
- $\Sigma$ ist eine Menge von Terminalen
- $P \subseteq (V \cup \Sigma)^{\star} \times (V \cup \Sigma)^{\star}$ ist eine Menge von Produktionen und legt den Aufbau von Woertern der Sprache fest
- $S \in V$ dient als Startpunkt fuer einen Ausdruck
###### Ableitungsrelationen
- In einer Grammatik koennen ueber Ableitungsrelationen $\rightarrow_G$ anhand von Produktionen Woerter erzeugt werden werden
- Die Menge aller Woerter, die von einer Grammatik erzeugt werden koennen, werden mit $L(G)$ beschrieben
###### Wortproblem
- Im Wortproblem muss festgestellt werden, ob ein Wort aus einer gegebenen Grammatik abgeleitet werden kann
#### Chomsky Hierarchie
- Grammatiken werden anhand bestimmter Kriterien hierarchisch angeordnet
###### Typ 0
- Die Anfoderungen einer Typ 0 Grammatik sind stets erfuellt
- Typ 0 Grammatiken sind Phrasenstrukturgrammatiken
###### Typ 1
- Eine Grammatik ist von Typ 1, falls fuer jede Produktion $\alpha \rightarrow \beta$, $|\beta| \geq |\alpha|$ gilt
- Typ 1 Grammatiken sind kontextsensitiv
###### Typ 2
- Eine Grammatik ist von Typ 2, falls sie Typ 1 ist und zudem fuer jede Produktion $\alpha \rightarrow \beta$, $\alpha \in V$ gilt
- Typ 2 Grammatiken sind kontextfrei
###### Typ 3
- Eine Grammatik ist von Typ 3, falls sie Typ 2 ist und zudem fuer jede Produktion $\alpha \rightarrow \beta$, $\beta \in \Sigma \cup \Sigma V$ gilt
- Typ 3 Grammatiken sind rechtslinear