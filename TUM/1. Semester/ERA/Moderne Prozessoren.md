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
#### [[Multithreading]]
## Speedup
- Der Speedup eines parallelen Programms ergibt sich aus der Relation der sequentiellen und der parallelen Laufzeit
- Ein paralleles Programm besteht stets aus sequentiellen und parallelen Abschnitten
#### Amdahl's law
- Beschreibt den moeglichen Speedup bei konstanter Problemgroesse
###### Berechnung
![[Pasted image 20230127141037.png]]
![[Pasted image 20230127141139.png]]
![[Pasted image 20230127141151.png]]
![[Pasted image 20230127141203.png]]
#### Gustafson's law
- Beschreibt den moeglichen Speedup bei proportionaler Problemgroesse
###### Berechnung
![[Pasted image 20230127143143.png]]
![[Pasted image 20230127143154.png]]