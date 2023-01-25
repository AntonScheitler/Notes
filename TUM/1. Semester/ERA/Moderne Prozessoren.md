## Out-of-Order Execution
- Bei der sequentiellen Befehlsverarbeitung in einem pipelined Prozessor kann es zu Hazards kommen
- Manche Hazards koennen ueber das umsortieren von Befehlen behoben werden
- Out-of-Order Prozessoren sind deutlich komplexer, bieten allerdings auch eine effizientere Nutzung von Parallelitaet
## Parallelitaet
#### Superskalaritaet
- Mehrere unabhaengige Maschinenbefehle koennen parallel ausgefuehrt werden
- Hierfuer verwendet der Prozessor mehrere Funktionseinheiten und Dekodierer
- Zudem werden Pipelinestufen nach der Art des Befehls unterschieden
###### Beispiel
![[Pasted image 20230125122843.png]]
#### VLIW Prozessoren
- Ein Instruktionswort enthaelt mehrere Befehle
- Diese Befehle sind unabhaengig voneinander und koennen parallel bearbeitet werden
###### Beispiel
![[Pasted image 20230125123922.png]]
#### SIMD
- Bei Single Instruction Multiple Data wird eine Operation parallel auf mehrere Datenstroeme angewandt
- Dies eignet sich besonders fuer Vektoroperationen
###### Beispiel
![[Pasted image 20230125125524.png]]
#### Multithreading
- Ein Hardware-Thread ist eine Ausfuehrungseinheit, welche aus einem Befehlszaehler und Registern besteht
- Andere Ressourcen, wie Speicher und Rechenwerke werden von Threads geteilt
- Ein Kern ist die Kombination aus Threads und den geteilten Ressourcen
- Kerne teilen sich wiederum die Cachehierarchie und arbeiten groesstenteils unabhaengig
- Multithreading Architekturen unterscheiden sich darin, wie sich Threads, Ressourcen teilen
###### Architekturen
- Einfaches Multithreading
	- Threads wechseln sich zu einem festen Takt ab
 - Simultaneous Multithreading
	 - Threads laufen echt parallel, falls sie unterschiedliche Teile der Ressourcen benoetigen
###### Beispiel
![[Pasted image 20230125155911.png]]