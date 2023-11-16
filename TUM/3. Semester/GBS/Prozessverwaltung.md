## Prozesszustaende
- Ein Prozess kann unterschiedliche Phasen durchlaufen, bevor er ausgefuehrt wurde
- Dies ist der Fall, da ein Prozess der CPU entzogen werden kann, oder auf die Festplatte ausgelagert wird
#### Beispiel
![[Pasted image 20231030080632.png]]
## Threading
- Ein Thread ist der Konstrollfluss eines Prozesses und wird durch Instruktionen vorgegeben
- In einem multithreaded Prozess laufen mehrere Threads parallel im selben Adressraum, aber mit eigenen Befehlszaehlern und Registern
#### Implementierungen
- Threads koennen auf unterschiedliche Weisen realisiert werden
###### User-Level Threads
- User-Level Threads werden mithilfe eines Laufzeitsystems in einem Prozess verwaltet
- Der [[Scheduling|Scheduler]] des Betriebssystem kann Threads jedoch nicht zuweisen
###### Kernel-Level Threads
- Kernel-Level Threads werden direkt von dem Betriebssystem verwaltet
- Da fuer das Arbeiten mit Threads in den Systemmodus gewechselt werden muss, steigt der Overhead
###### Beispiel
![[Pasted image 20231108162046.png]]
#### Beispiel
![[Pasted image 20231102100432.png]]
## Verwaltung
- Das Betriebssystem verwendet unterschiedliche Datenstrukturen, um Prozesse zu verwalten
#### Process Control Block
- In einem Process Control Block werden alle Informationen ueber Prozesse, wie Pointer auf Stack und Heap, die ProzessId und geoeffnete Dateien, verwaltet
#### Prozesstabelle
- Eine Prozesstabelle ist eine Liste von Process Control Blocks
- Es werden separate Listen fuer wartende, oder rechenwillige Prozesse angelegt
###### Beispiel
![[Pasted image 20231102101954.png]]
## Systemdienste fuer Prozesse
- Das Betriebssystem bietet unterschiedliche Dienste zum Arbeiten mit Prozessen
#### Prozesserzeugung
- Mithilfe des System Calls fork, kann ein Elternprozess ein Kindprozess erzeugen
- Der Kindprozess erbt das Text und das Data Segment seines Parents, kann dies jedoch auch ueberschreiben
- Die PID eines Kindprozesses ist stets 0, seine PPID referenziert seinen Parent
#### Prozessterminierung
- Ein Prozess kann freiwillig terminieren, oder bei fatalen Fehlern durch das Betriebssystem beendet werden
- Ein Elternprozess kann mithilfe von wait auf das Terminieren seiner Kindprozesse warten
- Terminiert ein Parent vor seinem Kindprozess, so wird init zum neuen Parent
## Dispatching
- Ein Dispatcher entzieht Prozessen die CPU, um sie anderen Prozessen zuzuweisen
#### Context Switch
- Der Kontext des vorherigen Prozesses wird im PCB gespeichert und der des neuen Prozesses vom PCB geladen
- Bei einem Wechsel zwischen Threads im selben Prozess ist allerdings kein Context Switch noetig
#### Beispiel
![[Pasted image 20231108162632.png]]