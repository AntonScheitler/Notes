## Spruenge
- Von dem Ablauf eines Programms kann ueber spruenge abgewichen werden
- Spruenge werden ueber den JMP Befehl, gefolgt von der Adresse ausgefuehrt
#### Beispiel

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
- Bei direkter Adressierung kann direkt auf eine konkrete Adresse zugegriffen werden
- Bei indirekter Adressierung kann auf eine Adresse, die in einem Register enthalten ist, zugegriffen werden
###### Beispiel
	.data
	var: DD 123
	
	.txt
	MOV ECX, var ; laedt die Adresse von var in ECX
	MOV EAX, [10] ; laedt den Inhalt der Adresse '10' in EAX
	MOV EBX, [ECX] ; laedt den Inhalt der Adresse, die ECX enthaelt
## Stack
- Der Stack wird genutzt, um Ruecksprungadressen und Registerinhalte zu speichern
- Das ESP Register deutet auf das oberste Element im Stack
- Daten koennen ueber PUSH und POP auf den Stack gelegt und vom Stack entfernt werden
#### Unterprogramme
- Unterprogramme koennen ueber den CALL Befehl ausgefuehrt werden