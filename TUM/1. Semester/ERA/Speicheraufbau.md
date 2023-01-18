## Allgemeines
- Ein Random Access Memory kann auf verschiedene Arten implementiert werden
- Hierfuer werden Matrizen aus Static RAM Zellen und Dynamic Ram Zellen verwendet
## SRAM
- Eine SRAM Zelle wird mithilfe von zwei Transistoren und zwei NOT Gates realisiert
- SRAM wird fuer Register und [[Cache|Caches]] verwendet
#### Schreiben
- Das Select Signal wird auf 1 gesetzt und die gewuenschten Bits an den Eingaengen der Zelle angelegt
- Die Eingaenge werden ueber die Transistoren in einen Zyklys aus NOT Gates geleitet und somit gespeichert
#### Lesen
- Beide Eingaenge der Zelle, sowie das Select Signal werden auf 1 gesetzt
- Durch den Spannungsabfall auf einer Seite der Schaltung, koennen die Bits ausgelesen werden
#### Vor- und Nachteile
- SRAM Speicher sind schnell und koennen Daten speichern, solange Strom anliegt
- Sie sind allerdings gross und energieintensiv
#### Beispiel
![[Pasted image 20230117113227.png]]
![[Pasted image 20230117114108.png]]
## DRAM
- Eine DRAM Zelle wird mithilfe eines Transistors und eines Kondensators realisiert
- DRAM wird fuer den [[Hauptspeicher]] verwendet
#### Schreiben
- Das Select Signal wird gesetzt und das gewuenschte Bit an den Eingang angelegt
- Das Bit wird ueber einen Transistor in einen Kondensator geleitet und dort gespeichert
#### Lesen
- Es werden immer ganze Zeilen eines DRAM Speichers ausgelesen
- Das Select Signal wird gesetzt und der Kondensator entlaedt sich, wodurch das Bit ausgelesen werden kann
- Der Inhalt einer Zelle wird somit durch das Auslesen zerstoert und der Kondensator entlaedt sich mit der Zeit
- Der Speicher muss somit regelmaessig und bei jedem Auslesen neu beschrieben werden
#### Vor- und Nachteile
- DRAM Speicher sind klein und einfach
- Speicherzugriffe sind recht zeitintensiv
#### Beispiel
![[Pasted image 20230117120833.png]]