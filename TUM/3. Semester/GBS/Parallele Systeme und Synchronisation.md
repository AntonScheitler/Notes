## Parallele Programme
- In einem parallelen Programm laufen mehrere Teile des Programms parallel zueinander
- Diese Programmteile koennen Aufgaben miteinander koordinieren, miteinander kommunizieren, oder um Ressourcen konkurrieren
#### Eigenschaften
- Ein paralleles System soll bei gleichen Eingaben zur selben Ausgabe fuehren
- Falls geteilte Ressourcen genutzt werden, muessen sich Prozesse beim Zugriff gegenseitig ausschliessen
- Deadlocks oder Lifelocks muessen verhindert werden
## Synchronisation
- Synchronisation von parallelen Systemen umfasst das Abstimmen nebenlaeufiger Aktivitaeten und das Koordinieren von Zugriffen auf geteilte Ressourcen
#### Race Conditions
- Versuchen zwei Prozesse zeitgleich auf eine Ressource zuzugreifen, so kommt es zu einer Race Condition
- Da es nicht absehbar ist, welcher der Prozesse zuerst auf die Ressource zugreift, ist das Verhalten nicht deterministisch
###### Beispiel
![[Pasted image 20231120150824.png]]