## Allgemeines
- Ein Cache dient als Zwischenspeicher zwischen dem [[Hauptspeicher]] und dem Prozessor
- Es kann nicht explizit auf den Inhalt eines Caches zugegriffen werden
- Stattdessen erfolgen Lese- und Schreiboperationen auf den Cache automatisch
## Aufbau
- Ein Cache ist in Zeilen organisiert, welche mehrere Teile haben
	- Ein Datenblock, der die eigentlichen Daten haelt
	- Ein Index, mit welchem die Zeile adressiert werden kann
	- Ein Tag, welches die Zeile eindeutig identifiziert
#### Arten
###### Direkt abbildene Caches
- Jede Zeile hat einen eigenen Index
###### Voll-assoziative Caches
- Zeilen haben keine Indizes
- Die Tag Bits werden mit jeder Zeile des Caches verglichen
###### Mengenassoziative Caches
- Mehrere Zeilen teilen sich einen Index
- Die Tag Bits werden mit jeder Zeile des Cache-Sets verglichen
## Lokalitaet
- Caches speichern Daten auf Grundlage der Lokalitaet
- Programme koennen optimiert werden, sodass sie das Lokalitaetsverhalten des Caches optimal ausnutzen
#### Zeitliche Lokalitaet
- Auf ein Datum wird in einem Zeitintervall haeufiger zugegriffen
#### Raeumliche Lokalitaet
- Auf benachbarte Daten wird haeufiger zugegriffen
## Lesezugriff
- Bei jedem Speicherzugriff wird geprueft, ob das gewuenschte Datum im Cache liegt
- Liegt das Datum im Cache, so wird es von dort geholt
- Liegt das Datum nicht im Cache, so kommt es zu einem Miss
#### Adressumrechnung
- Um den Cache zu lesen, muss eine Speicheradresse in eine Cachzeile uebersetzt werden
- Die Adresse wird in drei Teile aufgeteilt
	- Die Offset Bits bestimmen das Byte in einem Datenblock
	- Die Index Bits bestimmen die Cachezeilen in einem Cache
	- Die Tag Bits werden mit dem Tag einer Zeile verglichen
#### Cache Misses
- Im Falle eines Miss, werden die Daten aus dem Hauptspeicher in den Cache geladen
- Ist ein Cache voll, so koennen vorhandene Daten verdraengt werden
###### Compulsory Miss
- Auf eine Adresse wird zum ersten Mal zugegriffen
###### Conflict Miss
- Eine Adresse wurde verdraengt, da das Cache-Set voll war
###### Capacity Miss
- Eine Adresse wurde verdraengt, da die Kapazitaet des ganzen Caches voll ausgereizt wurde
## Prefetching
- Daten werden in den Cache geladen, bevor auf sie zugegriffen wird
- Prefetching kann ueber die Hardware oder die Software erfolgen
#### Hardware Prefetching
- Eine Hardwarekomponente sucht in Zugriffen nach Mustern und laedt die entsprechenden Daten
- Beispielsweise kann beim Laden einer Cachezeile auch die Folgezeile geladen werden
#### Software Prefetching
- Mithilfe expliziter Instruktionen kann ein Prefetch ausgefuehrt werden
- Prefetch Instruktionen werden in der Regel durch den Compiler ausgefuehrt
## Berechnung der Ausfuehrungszeit
![[Pasted image 20230120133849.png]]