## Prozesse in diskreter Zeit
- Ein stochastischer Prozess beschreibt eine zeitliche Folge von Zufallsexperimenten, die genutzt werden kann, um das Verhalten eines Systems zu beschreiben
- Zeit kann sowohl diskret, als auch kontinuierlich betrachtet werden
#### Markov-Ketten
- Eine Art von stochastischen Prozessen sind Markov-Ketten, bei denen der Zustand im $i+1$-ten Zeitschritt nur von Zustand im $i$-ten Zeitschritt und nicht der Historie von Zustaenden abhaengt
- Die Uebergangswahrscheinlichkeit $p_{ij}$ von einem Wechsel aus Zustand $i$ in Zustand $j$ kann somit beschrieben werden durch:
$$p_{ij} = Pr[X_{t + 1} = j \mid X_t = i]$$
- Ist der aktuelle Zustand $i$, so gilt zudem
$$\sum_{j \in S} p_{ij} = 1$$
###### Homogene Markov-Ketten
- Sind alle $p_{ij}$ von $t$ unabhaengig, so ist die Markov-Kette homogen
- Alle $p_{ij}$ koennen somit in einer Matrix $P$ notiert werden
- Ist $q_t$ ein Vektor, dessen $i$-te Komponente die Wahrscheinlichkeit beschreibt, dass sich die Kette nach $t$ Schritten im Zustand $i$ befindet, so gilt:
$$q_{t + 1} = P \cdot q_t$$
$$q_{t + k} = P^k \cdot q_t$$
- Ein Eintrag $p_{ij}$ in $P^k$ beschreiben hierbei die Wahrscheinlichkeit, dass Zustand $j$ von Zustand $i$ in $k$ Schritten erreicht wird
###### Veranschaulichung
- Eine Markovkette kann mithilfe eines Graphen veranschaulicht werden:
![[Pasted image 20240708102651.png]]
#### Ubergangszeiten und Ankunftswahrscheinlichkeiten 
- Die Uebergangszeit $T_{ij}$ ist die Anzahl der Schritte, die in einer Markov-Kette fuer den Weg von $i$ nach $j$ benoetigt werden, sodass:
$$T_{ij} = min\{n \geq 0 \mid X_n = j, \text{ wenn } X_0 = i\}$$
- Ferner ist $h_{ij} = \mathbb{E}[T_{ij}]$
- Die Ankunftswahrscheinlichkeit $f_{ij}$ beschreibt zudem die Wahrscheinlichkeit, dass $j$ nach beliebig vielen Schritten aus $i$ erreicht wird:
$$f_{ij} = Pr[T_{ij} < \infty]$$
###### Rueckkehrzeit
- Ein besonderer Fall der Uebergangszeit ist die Rueckkehrzeit, in der $i = j$, sodass:
$$T_{i} = min\{n \geq 1 \mid X_n = i, \text{ wenn } X_0 = i\}$$
- Die Rueckkehrwahrscheinlichkeit $f_i$ wird analog zur Ankunftswahrscheinlichkeit definiert:
$$f_i = Pr[T_i < \infty]$$
###### Berechnung
- Fuer den Erwartungswert der Uebergangszeit $T_{ij}$, beziehungsweise der Rueckkehrzeit $T_i$ gilt:
$$h_{ij} = 1 + \sum_{k \neq j} p_{ik} \cdot h_{kj} $$
$$h_{i} = 1 + \sum_{k \neq i} p_{ik} \cdot h_{ki} $$
- Die Ankunftswahrscheinlichkeiten sind somit definiert durch:
$$f_{ij} = p_{ij} + \sum_{k \neq j} p_{ik} \cdot f_{kj}$$
$$f_{i} = p_{ii} + \sum_{k \neq i} p_{ik} \cdot f_{ki}$$