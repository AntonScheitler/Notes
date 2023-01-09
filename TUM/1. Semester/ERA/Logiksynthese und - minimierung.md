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
###### Beispiel
![[Pasted image 20221220214131.png]]
#### Ueberdeckungsproblem
- Primimplikanten koennen einander ueberdecken
- Um ein optimales Minimalpolynom zu bilden, muessen geeignete Primimplikanten ausgewaehlt werden
###### Loesung des Uberdeckungsproblems
- In einer Primimplikantentafel werden Primimplikanten und Minterme, die von ihnen ueberdeckt werden, eingetragen
- Die geeigneten Primimplikanten werden durch Reduktion ausgewaehlt
	1. Wird ein Minterm nur durch einen Primimplikanten ueberdeckt, so werden der Minterm und der Primimplikant entfernt
	2. Dominierende Spalten werden entfernt
	3. Dominierte Zeilen werden entfernt
- Liefert die Primimplikantentafel kein Ergebnis, so kann das Verfahren von Petrick angewandt werden
	- Die verbleibenden Primimplikanten werden spaltenweise konjungiert und ausmultipliziert
	- Die minimalen Terme werden ausgewaehlt
###### Beispiel
![[Pasted image 20230109231022.png]]
![[Pasted image 20230109231035.png]]
![[Pasted image 20230109231058.png]]
![[Pasted image 20230109231110.png]]