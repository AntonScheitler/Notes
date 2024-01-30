## Allgemeines
- Transaktionen sind Datenuebertragungen mit bestimmten Eigenschaften
#### Eigenschaften
###### Atomicity
- Transaktionen werden entweder komplett oder garnicht ausgefuehrt
###### Consistency
- Transaktionen muessen die Integritaetsbedingungen der Datenbank erfuellen
###### Isolation
- Parallele Transaktionen beeinflussen sich nicht gegenseitig
###### Durability
- Aenderungen, die durch Transaktionen commited wurden, sind dauerhaft
#### Ausfuehrung
- Eine Transaktion wird mit begin-of-transaction eingeleitet
- War die Transaktion erfolgreich, so werden die Aenderungen ueber commit zurueckgeschrieben
- War sie es nicht, so werden die Aenderungen durch abort zurueckgesetzt
## Fehlerbehandlung
- Die Eigenschaften einer Transaktion muessen bei unterschiedlichen Fehlern geschuetzt bleiben
#### Fehlerklassifikation
- Je nach Fehlergrad, muss unterschiedlich gehandelt werden
###### Transaktionsfehler
- Falls es einen Fehler in einer einzelnen Transaktion gibt, kann diese durch abort abgebrochen werden, ohne, dass das System beeintraechtigt wird
###### Fehler mit Hauptspeicherverlust
- Falls der Datenbankpuffer des Hauptspeichers geloescht wird, kann es Daten geben, welche noch nicht in die Datenbank geschrieben wurden 
###### Fehler mit Hintergrundspeicherverlust
- Falls die Datenbank geloescht wird, muss der urspruengliche Zustand wiederhergestellt werden
#### Logs
- Durch Logs werden Transaktionen und ihre Auswirkungen protokolliert
- Anhand von Logs kann der Zustand der Datenbank nach Fehlern mit Speicherverlust wiederhergestellt werden
###### Before-Image
- Das before-image ist der Zustand vor der Ausfuehrung einer gegebenen Transaktion
- Das before-image kann somit durch das after-image und den Undo der Tranaktion generiert werden
###### After-Image
- Das after-image ist der Zustand nach der Ausfuehrung einer gegebenen Transaktion
- Das after-image kann somit durch das before-image und den Redo der Transaktion generiert werden 
###### Seiten Nummerierung
- Jede Seite speichert den Index des Log Eintrags, der sie referenziert
- Somit kann fuer jede Seite bestimmt werden, ob sie das before- oder das after-image repraesentiert
![[Pasted image 20240125114118.png]]
#### Rekonstruktion
- Die Rekonstruktion wird in mehrere Schritte aufgeteilt
###### Analyse
- Die Logs werden analysiert, um zu bestimmen, welche Transaktionen erneut ausgefuehrt werden sollen, und welche unterbochen wurden und rueckgaengig gemacht werden sollen
###### Rekonstruktion
- Alle Transaktionen, die in den Logs protokolliert wurden, werden erneut ausgefuehrt
###### Undo
- Aenderungen durch Transaktionen, die unterbrochen wurden, werden rueckgaengig gemacht