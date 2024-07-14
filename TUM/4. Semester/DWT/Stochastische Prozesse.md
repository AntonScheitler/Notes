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
$$q_{t + 1} = q_t \cdot P$$
$$q_{t + k} = q_t \cdot P^k $$
- Ein Eintrag $p_{ij}$ in $P^k$ beschreiben hierbei die Wahrscheinlichkeit, dass Zustand $j$ von Zustand $i$ in $k$ Schritten erreicht wird
- Ein Vektor $q_t$ wird hierbei wagrecht notiert
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
#### Stationaere Verteilung
- Eine Verteilung $\pi$ ist eine stationaere Verteilung mit der Eigenschaft:
$$\pi \cdot P = \pi$$
- $\pi$ ist somit ein Eigenvektor von $P^T$ zum Eigenwert $1$  
- Allgemein kann $\pi$ jedoch auch ueber das Loesen des linearen Gleichungssystems bestimmt werden
#### Eigenschaften von Markov-Ketten
- Markov-Ketten koennen unterschiedlich charakterisiert werden
###### Irreduzibilitaet
- Eine Markov-Kette ist irreduzibel, falls es fuer alle Zustandspaare $i, j$ ein $n \in \mathbb{N}$ gibt, sodass $p_{ij}^{(n)} > 0$
- Somit muss jeder Zustand ueber eine beliebige Anzahl an Schritten von jedem anderen Zustand erreicht werden koennen
- Jede irreduzible Markov-Kette besitzt eine stationaere Verteilung $\pi$
###### Aperiodizitaet
- Ein Zustand $i$ ist aperiodisch, falls es ein $n_0 \in \mathbb{N}$ gibt, sodass $\forall n \geq n_0: p_{ii}^{(n)} > 0$
- Damit $i$ aperiodisch ist, benoetigt der Zustand somit eine reflexive Kante, oder die Laengen der Kreispfade von $i$ sind teilerfremd
- Eine Markov-Kette ist aperiodisch, falls all ihre Zustaende aperiodisch sind
###### Ergodizitaet
- Irreduzible, aperiodische Markov-Ketten bezeichnet man als ergodisch
- Fuer jede ergodische Markov-Kette gilt:
$$\lim_{t \to \infty} q_t = \pi$$
#### Doppeltstochastische Matrizen
- Eine $P$ ist stochastisch, falls all ihre Eintraege $p_{ij}$ nichtnegativ und ihre Zeilensummen gleich $1$ sind
- Die Uebergangsmatrix einer Markov-Kette ist somit stets stochastisch
- $P$ ist doppeltstochastisch, falls zudem all ihre Spaltensummen gleich $1$ sind
###### Eigenschaften
- Ist $P$ eine doppeltstochastische $n \times n$ Matrix, so ist $\pi = \left(\frac{1}{n}, ..., \frac{1}{n} \right)$ eine stationaere Verteilung von $P$
- Fuer jede ergodische Markov-Kette mit einer doppeltstochastischen $n \times n$ Uebergangsmatrix gilt somit:
$$\lim_{t \to \infty} q_t = \left(\frac{1}{n}, ..., \frac{1}{n} \right)$$