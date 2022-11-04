## Allgemeines
#### Ein- und Zwei-Operanden Form
## Speicherzugriffe
- Da die Anzahl der Register beschraenkt ist, muss bei groesseren Datenmengen auf den [[Hauptspeicher]] zugegriffen werden
- Es kann jeweils separat auf 1, 2 oder 4 Byte zugegriffen werden
#### Speicherbereiche
- Speicher kann in Assembler ueber den RES befehl allokiert werden
- Man unterscheidet bei allokiertem Speicher, initialisierteund nicht initialisierten Speicherbereiche
- Fuer nicht initialisierten Speicher verwendet man im BSS Segment RESB, RESW, RESD oder RESQ
- Fuer initliaisierten Speicher verwendet man im Data Segment DB, DW, DD oder DQ, gefolgt von dem initialen Wert
###### Beispiel
	.bss
	syma: RESB 1 ; reserviert einen Byte unter dem Label 'syma'
	symb: RESW 1
	
	.data
	string: DB 72, 101, 108, 108, 111 ; speichert 'Hello'
	
	.text
	MOV EAX, syma ; laedt die Adresse von syma in EAX
	PRINT_STRING string ; laedt den Inhalt von string in die Ausgabe
#### Speicheradressierung
- Mithilfe direkter Adressierung kann ueber eine konkrete Adresse auf ein Datum zugegriffen werden
- 

## Unterprogramme