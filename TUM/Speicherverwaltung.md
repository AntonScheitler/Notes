## Speicherorganisation
- Jeder Prozess hat einen eigenen Platz im [[Hauptspeicher]], samt Stack, Heap, Data- und Codesegment
- Laufen mehrere Prozesse parallel, so muss das Betriebssystem, den Speicher eines Prozesses vor allen anderen schuetzen
#### Virtueller Adressraum
- Mithilfe eines virtuellen Adressraums kann der Speicher eines Prozesses geschuetzt werden
- Ein Prozess kann seinen virtuellen Adressraum beliebig nutzen, der Adressraum anderer Prozesse bleibt allerdings verborgen
- Fuer tatsaechliche Speicherzugriffe werden allerdings die physikalischen Adressen benoetigt
#### Memory Management Unit
- Um virtuelle Adressen in Physikalische zu uebersetzen, wird die Memory Management Unit verwendet
- Der Uebersetzungsprozess erfolgt mithilfe von Pages
###### Pages
- Ein [[Hauptspeicher]] wird in Pages fester Groesse eingeteilt
- In Page Tables werden virtuelle Adressen und ihre physikalischen Gegenstuecke gespeichert
###### Page Directory
- Ueber ein Page Directory wird auf die Page Tables eines Prozesses verwiesen
- Ein Spezialregister verweist wiederum auf das Page Directory
- Bei einem Prozesswechsel wird somit nur dieses Spezialregister veraendert