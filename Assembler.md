## Allgemeines
## Speicherzugriffe
- Da die Anzahl der Register beschraenkt ist, muss bei groesseren Datenmengen auf den [[Hauptspeicher]] zugegriffen werden
- Es kann jeweils separat auf 1, 2 oder 4 Byte zugegriffen werden
#### Speicherbereiche
- Speicher kann in Assembler ueber den **RES** befehl allokiert werden
- Man unterscheidet bei allokiertem Speicher, **initialisierte** und **nicht initialisierten** Speicherbereiche
- Fuer nicht initialisierten Speicher verwendet man im BSS Segment **RESB**, gefolgt von der Anzahl der Bytes
- Fuer initliaisierten Speicher verwendet man im Data Segment **DB**, gefolgt von dem initialen Wert
##### Beispiel

## Unterprogramme