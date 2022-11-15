## Spruenge
- Von dem Ablauf eines Programms kann ueber spruenge abgewichen werden
#### Unbedingte Spruenge
- Unbedingte Spruenge werden ueber den JMP Befehl, gefolgt von der Adresse ausgefuehrt
###### Beispiel
	JMP 0x1234 ; springt zum Befehl an der Adresse 0x1234
	JMP label1 ; springt zum Befehl, der mit label1 markiert ist
#### Bedingte Spruenge
- Bedingte Spruenge werden ausgehend von Statusregistern ausgefuehrt
- Statusregister werden durch den CMP Befehl beeinflusst, was einer Subtraktion ohne Aenderung der Operanden entspricht
- Unterschiedliche Sprungbefehle pruefen unterschiedliche Flags
###### Sprungbefehle
![[Pasted image 20221111135724.png]]
###### Beispiel
	.text
		CMP EAX, 0
		JE basisfall
		
		...
		
		basisfall:
			MOV EAX, 1
			RET	
## Speicherzugriffe
- Da die Anzahl der Register beschraenkt ist, muss bei groesseren Datenmengen auf den [[Hauptspeicher]] zugegriffen werden
- Es kann jeweils separat auf 1, 2 oder 4 Byte zugegriffen werden
#### Speicherbereiche
- Man unterscheidet bei allokiertem Speicher, initialisierte und nicht initialisierte Speicherbereiche
- Fuer nicht initialisierten Speicher verwendet man im BSS Segment RESB, RESW, RESD oder RESQ, gefolgt von der Anzahl der Woerter
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
- Der Stack wird genutzt, um Ruecksprungadressen und Registerinhalte zu sichern
- Das ESP Register deutet auf das oberste Element im Stack
- Das EBP Register deutet auf dieselbe Adresse wie ESP zu Beginn des Unterprogramms
- Daten koennen ueber PUSH und POP auf den Stack gelegt und vom Stack entfernt werden
#### Unterprogramme
- Unterprogramme koennen ueber den CALL Befehl ausgefuehrt werden
- Durch CALL wird ein Sprung ausgefuehrt und die Ruecksprungadresse auf dem Stack gespeichert
- Mithilfe von RET kann wieder zurueck an die Ruecksprungadresse gesprungen werden
###### Aufrufkonvention
- Um einen effektiven Aufruf von Unterprogrammen zu garantieren, muss die Aufrufkonvention eingehalten werden
	- Parameter werden in umgekehrter Reihenfolge durch den Caller auf den Stack gelegt, bevor CALL ausgefuehrt wird
	- Der Rueckgabewert wird ueber das EAX Register uebergeben
- Um Registerinhalte vor Aenderungen zu schuetzen, werden Caller- und Callee-Saved Register definiert
	- Caller-Saved Register werden vom aufrufenden Programm gesichert
	- Callee-Saved Register werden vom aufgerufenen Programm gesichert
###### Beispiel
	.text
		MOV EAX, 0
		CALL unterprogramm

		unterprogramm:
			ADD AX, 10
			RET