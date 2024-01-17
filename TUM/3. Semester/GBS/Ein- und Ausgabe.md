## Ein- und Ausgabegeraete
- Ein-/Ausgabegeraete unterscheiden sich stark, muessen jedoch unter einer einheitlichen Schnittstelle bereitgestellt werden
#### Device Controller
- Ein Device Controller besitzt Steuerregister und Datenpuffer, in welche das Betriebssystem schreiben kann
- Hierdurch kann mit einem Ein-/Ausgabegeraet kommuniziert werden
###### Programmed IO
- Die CPU kommuniziert direkt mit dem Geraet und wartet aktiv auf Antworten
- Die CPU wird somit durch die I/O blockiert
###### Direct Memory Access
- Die CPU gibt Parameter wie Speicheradressen an einen DMA Controller
- Der DMA Controller initiiert die Uebertragung von Geraetedaten in den Hauptspeicher
- Ist der Transfer abgeschlossen, so wird der DMA Controller informiert und die CPU unterbrochen
###### Beispiel
![[Pasted image 20240117180920.png]]
## Geraetesoftware
- Um effektiv Befehle an ein Geraet uebermitteln zu koennen, werden Geraetesoftware, sowie eine einheitliche Schnittstelle benoetigt 
#### Geraetetreiber
- Die Treiber fuer ein Geraet gehoeren zum Betriebssytem
- Treiber fuehren geraetespezifische Software aus, indem sie mit den Controllern der Geraete kommunizieren
- Es muss sichergestellt werden, dass Treiber eine einheitliche Schnittstelle zum Rest des Betriebssystems ueber Funktionen wie open, read, write und close bieten
###### Beispiel
![[Pasted image 20240117180844.png]]
#### Spooler
- Sind Geraete nur exklusiv nutzbar, so werden Zugriffe durch einen Spooler Daemon verwaltet
- Der Spooler verwaltet hierbei Auftraege und interagiert mit dem Treiber des Geraets