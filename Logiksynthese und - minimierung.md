## Logiksynthese
- Grundlage fuer jeden Schaltkreis sind boolsche Funktionen
- Das Ein- und Ausgabeverhalten eines Schaltkreises muss somit in eine boolsche Funktion umschrieben werden 
#### Schaltkreiskonstruktion
- Eine boolsche Funktion kann in eine disjunktive und konjunktive Normalform gebracht werden
- Der eigentliche Schaltkreis wird nun mit einer Kombination aus Negation, Konjunktion und Disjunktion konstruiert
###### Beispiel
![[Pasted image 20221220214034.png]]
## Logikminimierung
- Zwar kann jede beliebige boolsche Funktion in eine Normalform gebracht und so realisiert werden, jedoch koennen durch Optimierungen, Kosten reduziert werden
#### Generierung von Primimplikanten
- Implikanten koennen mithilfe des Quine-McCluskey Verfahrens zu Primimplikanten minimiert werden
- Zwei Implikanten koennen gekuerzt werden, falls sie sich in der Negation von genau einem Literal unterscheiden
- Eine boolsche Funktion kann ueber die Disjunktion von Primimplikanten realisiert werden
###### Auswahl von Primimplikanten
- Primimplikanten koennen einander ueberdecken
- Um ein optimales Minimalpolynom zu bilden, muessen die Primimplikanten so gewaehlt werden, dass ueberdeckte Primimplikanten nicht aufgenommen werden
###### Beispiel
![[Pasted image 20221220214131.png]]