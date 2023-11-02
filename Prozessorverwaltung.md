## Prozesszustaende
- Ein Prozess kann unterschiedliche Phasen durchlaufen, bevor er ausgefuehrt wurde
- Dies ist der Fall, da ein Prozess der CPU entzogen werden kann, oder auf die Festplatte ausgelagert wird
#### Beispiel
![[Pasted image 20231030080632.png]]
## Scheduling
- Scheduling ist das Vorgehen, nachdem Prozesse der CPU zugewiesen werden
#### Multiprogramming
- Da unterschiedliche Prozesse unterschiedliche Ressourcen benoetigen, wird ihre Ausfuehrungsreihenfolge misachtet, um die CPU Auslastung zu erhoehen
- Somit koennen CPU intensive Prozesse ausgefuehrt werden, waehrend ein anderer Prozess mit der I/O interagiert
## Threading
- Ein Thread ist der Konstrollfluss eines Prozesses und wird durch Instruktionen vorgegeben
- In einem multithreaded Prozess laufen mehrere Threads parallel im selben Adressraum, aber mit eigenen Befehlszaehlern und Registern
#### Performanz
- Das Erzeugen von Threads ist mit einem Overhead verbunden, der jedoch nicht so gross ist, wie beim Erzeugen von Prozessen
- Mithilfe von Multithreading koennen Programmabschnitte parallel ausgefuehrt werden
#### Beispiel
![[Pasted image 20231102100432.png]]
## Verwaltung
- Das Betriebssystem verwendet unterschiedliche Datenstrukturen, um Prozesse zu verwalten
#### Process Control Block
- In einem Process Control Block werden alle Informationen ueber Prozesse, wie Adressen des Stack und Heap, die ProzessId und geoeffnete Dateien, verwaltet
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
- Die PID eines Kindprozesses ist stets 0