## Ein- und Ausgabegeraete
- Ein-/Ausgabegeraete unterscheiden sich stark, muessen jedoch unter einer einheitlichen Schnittstelle bereitgestellt werden
#### Device Controller
- Ein Device Controller besitzt Steuerregister und Datenpuffer, in welche das Betriebssystem schreiben kann
- Hierdurch kann mit einem Ein-/Ausgabegeraet kommuniziert werden
###### Programmed IO
- Die CPU kommuniziert direkt mit dem Geraet und wartet aktiv auf Antworten
- Die CPU wird somit durch die I/O blockiert
- Bei kurzer Kommunikation ist dies jedoch effizienter
###### Direct Memory Access
- Die CPU gibt Parameter wie Speicheradressen an einen DMA Controller
- Der DMA Controller initiiert die Uebertragung von Geraetedaten in den Hauptspeicher
- Ist der Transfer abgeschlossen, so wird der DMA Controller durch das Geraet informiert und unterbricht die CPU
- Hierdurch muss die CPU die Daten nicht selbst in den Hauptspeicher laden und wird weniger oft unterbrochen
###### Beispiel
![[Pasted image 20240117180920.png]]
## Geraetesoftware
- Um effektiv Befehle an ein Geraet uebermitteln zu koennen, werden Geraetesoftware, sowie eine einheitliche Schnittstelle benoetigt 
#### Geraetetreiber
- Die Treiber fuer ein Geraet gehoeren zum Betriebssytem
- Treiber fuehren geraetespezifische Software aus, indem sie mit den Controllern der Geraete kommunizieren
- Es muss sichergestellt werden, dass Treiber durch geraeteunabhaengige Software eine einheitliche Schnittstelle zum Rest des Betriebssystems ueber Funktionen wie open, read, write und close bieten
###### Beispiel
![[Pasted image 20240117180844.png]]
#### Spooler
- Sind Geraete nur exklusiv nutzbar, so werden Zugriffe durch einen Spooler Daemon verwaltet
- Der Spooler verwaltet hierbei Auftraege und interagiert mit dem Treiber des Geraets
## Geraete
- Geraete bieten zusaetzliche Funktionen fuer einen Rechner
- Man unterscheidet grundsaetzlich Blockorientierte Geraete, deren Inhalte adressierbar sind und Zeichenorientierte Geraete, welche Daten seriell transferieren
#### Festplatten
- Auf Festplatten koennen Daten permanent gespeichert werden
###### Aufbau
- Eine Festplatte ist in Platten aufgeteilt, die aus Tracks, welche wiederum aus Sektoren bestehen
- Uebereinanderliegende Tracks bilden einen Zylinder
- Die Daten werden verschraenkt in Sektoren gespeichert
![[Pasted image 20240123153824.png]]
###### Seek
- Der Abstand von Zylindern beeinflusst die Dauer von Lesezugriffen
- Um die Effizienz und Fairness zu erhoehen, kann in unterschiedlichen Reihenfolgen auf die Zylinder zugegriffen werden
![[Pasted image 20240123153800.png]]
###### RAID Systeme
- Bei RAID Systemen werden redundante Platten angelegt, um die Ausfallsicherheit, sowie die Zugriffsgeschwindigkeit zu erhoehen
- Die zusaetlichen Platten werden hierbei zu einem einzelnen Laufwerk virtualisiert
#### Solid-State Drives
- SSDs bieten groessere Fehlertoleranz und schnellere Zugriffszeiten als Laufwerke, koennen jedoch nur begrenzt oft beschrieben werden 
###### Write Amplification
- Um die Abnutzung beim Schreiben auszugleichen, wird das wear leveling angewandt
- Beim Ueberschreiben eines Blocks werden die, noch gueltigen, Daten kopiert und der gesamte Block geloescht
- Die neuen, sowie die noch gueltigen, Daten werden in einen neuen Block geschrieben
#### Timer
- Timer werden genutzt, um den Zeitablauf zu erfassen und sind somit relevant fuer Scheduling und Profiling
- Timer koennen hierbei auf unterschiedliche Arten realisiert werden
###### Hardware-Timer
- Der Hardware-Timer wird im Systemmodus gesetzt und generiert einen Interrupt, sobald er auslaeuft
- Somit sind Hardware-Timer genauer, koennen jedoch durch die staendigen Interrputs ein Programm verlangsamen
###### Soft-Timer
- Soft-Timer laufen nur, wenn ein Programm im Systemmodus ist
- Laeuft ein Soft-Timer aus, so kann ein Event behandelt werden, ohne, dass ein Interrupt noetig ist
- Soft-Timer sind somit effizienter, jedoch auch ungenauer