## Allgemeines
- Die Instruction Set Architecture bietet die Schnittstelle zwischen dem Programmierer und dem Rechner
- Die Kommunikation erfolgt mithilfe von [[Assembler]]
- Die ISA umfasst Informationen ueber Ausfuehrungsmodelle, den Prozessor und seine Register, sowie den Befehlssatz
## Ausfuehrungsmodelle
- Das Ausfuehrungsmodell beschreibt die Anzahl der Operanden, die in einem Befehl kodiert sind
	- **Stack Modell** (Alle Operanden sind durch den Stack impliziert)
	- **Akkumulator Modell** (Ein Operand, sowie das Ergebnis werden in den Akkumulator geladen)
	- **Register Modell** (Beide Operanden werden uebergeben, wobei einer vom Ergebnis ueberschrieben wird)
	- **Register-Register Modell** (Alle Operanden, sowie das Ergebnisregister werden separat spezifiziert)
## Befehlssatz
- Der Befehlssatz ist die Menge an Befehlen, mit der der Programmierer mit einem Rechner interagieren kann
- Man unterscheidet drei Klassen von Befehlen
	- Arithmetische und logische Operationen
	- Befehle fuer den Datentransfer, welche Daten aus und in den [[Hauptspeicher]] laden
	- Sprungbefehle, welche den Befehlszaehler ausgehend von Statusregistern aendern koennen
#### Complex Instruction Set Architecture (CISC)
- Grosser, komplexer Befehlssatz
- CISC Rechner werden durch Mikroprogramme realisiert
- Viele Befehle bleiben allerdings ungenutzt und sind meist langsamer
#### Reduced Instruction Set Architecture (RISC)
- Kleiner, elementarer Befehlssatz
- RISC Rechner werden durch feste Verdrahtung realisiert
- Die Befehle sind einfach und schnell ([[RISC-V]])