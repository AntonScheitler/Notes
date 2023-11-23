## Parallele Programme
- In einem parallelen Programm laufen mehrere Teile des Programms parallel zueinander
- Diese Programmteile koennen Aufgaben miteinander koordinieren, miteinander kommunizieren, oder um Ressourcen konkurrieren
#### Eigenschaften
- Ein paralleles System soll bei gleichen Eingaben zur selben Ausgabe fuehren
- Falls geteilte Ressourcen genutzt werden, muessen sich Prozesse beim Zugriff gegenseitig ausschliessen
- Deadlocks oder Lifelocks muessen verhindert werden
## Synchronisation
- Synchronisation von parallelen Systemen umfasst das Abstimmen nebenlaeufiger Aktivitaeten und das Koordinieren von Zugriffen auf geteilte Ressourcen
#### Race Condition
- Versuchen zwei Prozesse zeitgleich auf eine Ressource zuzugreifen, so kommt es zu einer Race Condition
- Da es nicht absehbar ist, welcher der Prozesse zuerst auf die Ressource zugreift, ist das Verhalten nicht deterministisch
###### Beispiel
![[Pasted image 20231120150824.png]]
#### Wechselseitiger Ausschluss
- In einem kritischen Pfad muessen sich Prozesse gegenseitig ausschliessen, um Race Conditions zu verhindern
###### Atmoare Operationen
- Atomare Operationen bestehen zwar aus mehreren Schritten, werden jedoch als eine Operation behandelt und koennen nicht unterbrochen werden
- Diese Operationen dienen als Grundlage fuer weitere Synchronisationsmethoden
###### Semaphoren
- Semaphoren sind Ganzzahlen welche atomar inkrementiert und dekrementiert werden koennen
- Wird versucht eine Semaphore zu dekrementieren, deren Wert $0$ ist, so muss der Prozess warten
###### Mutexe
- Mutexe sind Locks, mit denen kritische Abschnitte definiert werden koennen
###### Monitor
- Zugriffe auf geteilte Ressourcen werden durch einen Monitor verwaltet, welcher die Prozesse synchronisiert
- Die Synchronisation wird mithilfe von Semaphoren erreicht