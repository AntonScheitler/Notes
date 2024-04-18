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
- $P \subseteq (V \cup \Sigma)^{\star} \times (V \cup \Sigma)^{\star}$ ist eine Menge von Projektionen und legen den Aufbau von Woertern der Sprache fest
- $S \in V$ dient als Startpunkt fuer einen Ausdruck
###### Ableitungsrelationen
- In einer Grammatik koennen ueber Ableitungsrelationen $\rightarrow_G$ anhand von Projektionen Woerter erzeugt werden werden
- Die Menge aller Woerter, die von einer Grammatik erzeugt werden koennen, werden mit $L(G)$ beschrieben
###### Wortproblem
- Im Wortproblem muss festgestellt werden, ob ein Wort aus einer gegebenen Grammatik abgeleitet werden kann