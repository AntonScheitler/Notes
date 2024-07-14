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
- Ein Verifikator, der ueberprueft ob eine gegebene Loesung fuer das Problem korrekt ist, laeuft somit in polynomieller Zeit 
- Genauer ist es die Menge der Sprachen $A$, fuer die fuer alle $w \in A$ das Wortproblem von einer nichtdeterministischen Turing Maschine in $O(n^k)$ geloest werden kann
- Zwar ist $\mathbf{P} \subseteq \mathbf{NP}$, es ist jedoch unklar, ob $\mathbf{P} = \mathbf{NP}$
## $\mathbf{NP}$ Vollstaendigkeit
- $\mathbf{NP}$ vollstaendige Probleme sind die schwersten Probleme in $\mathbf{NP}$, wobei jedes andere Problem in $\mathbf{NP}$ auf ein solches Problem polynomiell reduziert werden kann
- Um $\mathbf{P} = \mathbf{NP}$ zu zeigen, muesste somit gezeigt werden, dass ein $\mathbf{NP}$ vollstaendiges Problem in $\mathbf{P}$ liegt
#### $\mathbf{NP}$ Haerte
- Eine Sprache $L$ ist $\mathbf{NP}$ hart, genau dann, wenn fuer alle $A \in \mathbf{NP}: A \leq_p L$ moeglich ist
- Um $\mathbf{NP}$ vollstaendig zu sein, muss zudem $L \in \mathbf{NP}$
#### Aussagenlogik
- Fuer eine aussagenlogische Formel $F$ beschreibt SAT das Problem, ob $F$ eine erfuellende Belegung besitzt
- SAT kann zudem auf 3SAT reduziert werden, welches sich nur mit konjunktiven Normalformen beschaeftigt, deren Klauseln hoechstens 3 Literale besitzen
- SAT, beziehungsweise 3SAT, ist ein NP vollstaendiges Problem