## Compilierte Sprachen
- Um aus einem Hochsprachenprogramm eine ausfuehrbare Datei zu erstellen muessen mehrere Schritte durchlaufen werden
#### Praeprozessor
- Ueber den Praeprozessor werden, unter Anderem, textuelle Ersetzungen von Macros durchgefuehrt, welche das Compilieren ermoeglichen
- Die resultierende Datei ist hierbei immernoch in der Hochsprache
#### Compilieren
- Mithilfe eines Compilers kann eine Hochsprachendatei in eine Assemblerdatei uebersetzt werden
#### Assemblieren
- Eine Assemblerdatei wird mithilfe eines Assemblers in eine Objektdatei uebersetzt
- Hierbei wird [[Assembler]]- in Binaercode umgewandelt
- Das Assemblieren laesst sich in zwei Laeufe einteilen
	- Im ersten Lauf werden die Adressen von Befehlen identifiziert und eine Opcode Tabelle erstellt
	- Im zweiten Lauf werden Programmfehler erkannt und die Objektdatei erstellt
#### Linker
- Um mehrere Objektmodule zu kombinieren, werden Linker verwendet
- Die Objektmodule werden verknuepft und auf einen virtuellen Adressraum abgebildet
- Da Adressen innerhab eines Objektmoduls nun nicht mehr korrekt sind, muss die Anfangsadresse des Moduls auf jede Speicheradresse aufaddiert werden
- Man unterscheidet statische und dynamische Bibliotheken
	- Eine statische Bibliothek wird direkt in die Binaerdatei eingebunden
	- Eine dynamische Bibliothek wird bei Bedarf vom Betriebssystem geladen und bei der Programmausfuehrung eingebunden 
###### Beispiel
![[Pasted image 20221114211241.png]]
#### Loader
- Der Loader ist der Teil des Betriebssystems, der beim Starten eines Programms ausgefuehrt wird
- Es werden ein neuer Adressraum fuer den Prozess angelegt, Bibliotheken geladen, der Linker ausgefuehrt und in das korrekte Laufzeitsystem gesprungen
#### Laufzeitsystem
- Ein Prozess benoetigt ein Laufzeitsystem, um ausgefuehrt werden zu koennen
- Das Laufzeitsystem umfasst [[Speicherverwaltung]] und Bibliotheken, sowie Schnittstellen zum Betriebssystem
#### Beispiel
![[Pasted image 20221114120856.png]]
## Interpretierte Sprachen
- Das Hochsprachenprogramm wird vom Interpreter schrittweise gelesen und abgearbeitet
- Kommandos in der Quelldatei loesen Funktionen im Interpreter aus
- Der Interpreter ist dynamisch und protabel, interpretierte Sprachen laufen jedoch langsamer