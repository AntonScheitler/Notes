## Allgemeines
- In der Komplexitaetstheorie wird mit der Komplexitaet von Problemen, nicht von Algorithmen gearbeitet
#### Zentrale Komplexitaetsklassen
- Probleme koennen anhand ihrer Komplexitaet in Klassen unterteilt werden
###### Komplexitaetsklasse $\mathbf{P}$
- Die Klasse $\mathbf{P}$ beschreibt alle Probleme, die von einer deterministischen Turing Maschine in polynomieller Zeit geloest werden koennen
- Genauer ist es die Menge der Sprachen $A$, fuer die das Wortproblem von einer deterministischen Turing Maschine in $O(n^k)$ geloest werden kann
- Dass ein Problem in $\mathbf{P}$ liegt, kann durch das Angeben eines entsprechenden Algorithmus geloest werden
###### Komplexitaetsklasse $\mathbf{NP}$
- Die Klasse $\mathbf{NP}$ beschreibt alle Probleme, die von einer nichtdeterministischen Turing Maschine in polynomieller Zeit geloest werden koennen
- Genauer ist es die Menge der Sprachen $A$, fuer die fuer alle $w \in A$ das Wortproblem von einer nichtdeterministischen Turing Maschine in $O(n^k)$ geloest werden kann
- Ein Problem liegt in $\mathbf{NP}$, falls es einen Verifikator gibt, der in polynomieller Zeit ueberprueft ob eine gegebene Loesung fuer das Problem korrekt ist
- Zwar ist $\mathbf{P} \subseteq \mathbf{NP}$, es ist jedoch unklar, ob $\mathbf{P} = \mathbf{NP}$
## $\mathbf{NP}$ Vollstaendigkeit
- $\mathbf{NP}$ vollstaendige Probleme sind die schwersten Probleme in $\mathbf{NP}$, wobei jedes andere Problem in $\mathbf{NP}$ auf ein solches Problem polynomiell reduziert werden kann
- Um $\mathbf{P} = \mathbf{NP}$ zu zeigen, muesste somit gezeigt werden, dass ein $\mathbf{NP}$ vollstaendiges Problem in $\mathbf{P}$ liegt
#### $\mathbf{NP}$ Haerte
- Eine Sprache $L$ ist $\mathbf{NP}$ hart, genau dann, wenn fuer alle $A \in \mathbf{NP}: A \leq_p L$ moeglich ist
- Um $\mathbf{NP}$ vollstaendig zu sein, muss zudem $L \in \mathbf{NP}$
#### Aussagenlogik
- Fuer eine aussagenlogische Formel $F$ beschreibt SAT das Problem, ob $F$ eine erfuellende Belegung besitzt
- SAT kann zudem in polynomieller Zeit auf 3KNF-SAT reduziert werden, welches sich nur mit konjunktiven Normalformen beschaeftigt, deren Klauseln hoechstens 3 Literale besitzen
- SAT, beziehungsweise 3KNF-SAT, ist ein NP vollstaendiges Problem
###### Reduktion
- Um ein Problem $P$ ueber aussagenlogische Formeln auf ein anders Problem $P'$ zu reduzieren, muss die Eingabe von $P$ so zu einer Eingabe von $P'$ umgewandelt werden, dass $P'$ genau dann geloest ist, wenn $P$ geloest ist
#### Mengenueberdeckung
- Gegeben eine Menge von Teilmengen $T_i$, eine Zielmenge $M$, sowie ein Limit $k$, beschreibt das Mengenueberdeckungsproblem, das Problem, ob es hoechstens $k$ Teilmengen gibt, die vereinigt $M$ ergeben
- Dieses Problem ist $\mathbf{NP}$ vollstaendig, da KNF-SAT hierauf reduziert werden kann
- Um das minimale $k$ zu bestimmen, kann binary search emuliert und das Mengenueberdeckungsproblem $\log(n)$ mal geloest werden- Ein Problem liegt in $\mathbf{NP}$, falls es einen Verifikator gibt, der in polynomieller Zeit ueberprueft ob eine gegebene Loesung fuer das Problem korrekt ist