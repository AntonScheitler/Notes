## Erzeugen einer ausfuehrbaren Datei
- Um aus einem Hochsprachenprogramm eine ausfuehrbare Datei zu erstellen, muss diese praeprozessiert, compiliert, assembliert und gelinkt werden
#### Praeprozessor
- Ueber den Praeprozessor werden unter Anderem textuelle Ersetzungen von Macros durchgefuehrt, welche das Compilieren ermoeglichen
- Die resultierende Datei ist hierbei immernoch in der Hochsprache
#### Compilieren
- Mithilfe eines Compilers kann eine Quelldatei in einer Hochsprache in eine [[Assembler]]datei uebersetzt werden
#### Assemblieren
- Eine [[Assembler]]datei wird mithilfe eines Assemblers in eine Objektdatei uebersetzt
- In diesem Schritt werden Fehler im Hochsprachenprogramm bekannt
#### Linker
- Um mehrere Objektdateien zu verknuepfen, koennen diese mithlife eines Linkers zu einer ausfuehrbaren Datei kombiniert werden
#### Beispiel
![[Pasted image 20221114120856.png]]
## Laufzeitumgebung
- Ein Programm benoetigt eine Laufzeitumgebung, um ausgefuehrt werden zu koennen
- Die Laufzeitumgebung umfasst [[Speicherverwaltung]], Bibliotheken und Betriebssysteme
## Interpretierte Sprachen
- Die Quelldatei in einer Hochsprache wird vom Interpreter schrittweise gelesen und abgearbeitet
- Kommandos in der Quelldatei loesen hierbei Funktionen im Interpreter aus
- Der Interpreter ist dynamisch und protabel
- Interpretierte Sprachen laufen jedoch langsamer