## Aufbau
- Ein Speicher ist eine Menge von Zellen fester Wortlänge
- Sämtliche Zellen haben eine Adresse und einen Wert
- Ein Speicher wird in einen Stack, Heap, Data und Code Segment eingeteilt
	- Ruecksprungadressen und Registerinhalte koennen im Stack gespeichert werden
	- Speicher im Heap kann dynamisch angefragt und freigegeben werden
	- Das Data Segment enthaelt festgelegte, globale Daten
	- Das Code Segment enthaelt das eigentliche Programm
#### Beispiel
![[Pasted image 20221025170103.png]]
## Datenzugriff
- Zugriffe auf Daten werden über das Memory Access Register und das Memory Data Register verwaltet
- Über das MAR wird die gewünschte Zelle adressiert
- Über das MDR können Daten gelesen oder überschrieben werden
- Auch wenn ein Speicher in Zellen mit fester Wortlaenge eingeteilt ist, sind dennoch Lese- und Schreiboperationen auf zellenuebergreifende Daten moeglich
#### Beispiel
![[Pasted image 20221024152907.png]]

## Ausrichtung von Daten
- Ein Datum der Größe n Byte ist korrekt ausgerichtet, falls für seine Adresse A gilt: A mod n = 0
- Da ein Speicher in Worten organisiert ist, werden bei korrekter Ausrichtung die Anzahl der Speicherzugriffe minimiert
- Inkorrekte Ausrichtung bietet effizientere Speichernutzung, führt allerdings neben mehr Speicherzugriffen auch zu einem höheren Hardwareaufwand
#### Endianness
- Endianness beschreibt die Reihenfolge von Bytes in einem Datum
- Bei Little Endian stehen signifikantere Bytes an höheren Adressen
- Bei Big Endian stehen signifikantere Bytes an niedrigeren Adressen
