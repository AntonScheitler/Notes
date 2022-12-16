## Allgemeines
- Statt ganze Instruktionen in einem Takt abzuarbeiten, wird die [[Befehlsverarbeitung]] in mehrere Schritte mit kuerzerem Takt unterteilt
- Eine Instruktion benoetigt somit mehrere Takte zum durchlaufen
- Die Taktgeschwindigkeit kann weiter erhoeht und einfache Befehle schneller bearbeitet werden
## Realisierung
- Multicycle Prozessoren werden mithilfe von [[Endliche Automaten|endlichen Automaten]] realisiert
- Je nach auszufuehrendem Befehl, wechselt der Prozessor in unterschiedliche Zustaende
#### Zustaende
![[Pasted image 20221216135920.png]]
#### Beispiel
![[Pasted image 20221213172856.png]]