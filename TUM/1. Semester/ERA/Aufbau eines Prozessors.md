## Komponenten
#### Program Counter
- Mithilfe des Program Counters wird die Adresse des naechsten auszufuehrenden Befehls gespeichert
###### Beispiel
![[Pasted image 20221206161821.png]]
#### Instruktionsspeicher
- Erhaelt als Eingang eine Adresse und liefert einen Befehl
###### Beispiel
![[Pasted image 20221206161829.png]]
#### Registerbank
- Die Registerbank ist die Menge aller Register
- Mithilfe von zwei Ports werden die Operanden ausgewaehlt und weitergegeben
- Mithilfe eines dritten Ports kann ein Register fuer das Speichern eines Werts ausgewaehlt werden
###### Beispiel
![[Pasted image 20221206162213.png]]
#### Arithmetic Logic Unit
- Gibt ausgehend von zwei Operanden und einem Kontrollsignal das Ergebnis einer Operation aus ([[Arithmetische und Logische Operationen]])
###### Beispiel
![[Pasted image 20221206162000.png]]
#### Datenspeicher
- Mithilfe einer Adresse kann ein Datum aus und in den Speicher geladen werden ([[Hauptspeicher]])
###### Beispiel
![[Pasted image 20221206162057.png]]
## Realisierung eines R-Typ Befehls
1. Der Ausgang des Program Counters wird an das Instruktionsregister angelegt
2. Die Adressbits der Operanden und des Ergebnisses werden aus der Instruktion ausgelesen und an die Registerbank angelegt
3. Die restlichen Bits der Instruktion werden an die Control Unit angelegt und in das Steuersignal der ALU, sowie in ein Enable Signal der Registerbank uebersetzt
4. Die beiden Operanden, sowie das Steuersignal steuern nun die ALU an
5. Das Ergebnis der Operation wird in die Registerbank zurueckgeschrieben
6. Mithilfe eines einfachen Addierers wird der Program Counter inkrementiert
#### Beispiel
![[Pasted image 20221206164229.png]]
## Prozessorerweiterungen
#### I-Typ
###### Immediates
- Die 12 Bits des Immediates werden mithilfe eines Extend Bausteins in eine 32 Bit Zahl ueberfuehrt
- Die Control Unit leitet je nach Opcode das Immediate, oder den Registerinhalt weiter
###### Load
- Der Ausgang der ALU wird als Adresse an den Datenspeicher angelegt
- Die Control Unit steuert, ob das Ergebnis der ALU, oder der Inhalt des Datenspeichers weitergeleitet wird
###### Beispiel
![[Pasted image 20221206170720.png]]
#### S-Typ
- An den Eingang des Extend Bausteins, werden nun ebenfalls die Immediate Bits des S-Typs angelegt
- Die Control Unit steuert, welche Immediate Bits erweitert werden
- Einer der Operanden wird an den Schreibeingang des Datenspeichers angelegt
###### Beispiel
![[Pasted image 20221206172301.png]]
#### B-Typ
- Die Flags der ALU werden an die Control Unit angelegt
- Das erweiterte Immediate wird mit dem Program Counter verrechnet
- Die Control Unit steuert, ob dieser Program Counter, oder der regulaer inkrementierte weitergegeben wird
###### Beispiel
![[Pasted image 20221207230007.png]]
#### J-Typ
- Der regulaer inkrementierte Program Counter wird ueber einen Multiplexer mit dem Schreibeingang der Registerbank verknuepft
- Mit der Control Unit wird gesteuert, ob das Ergebnis der ALU, der Inhalt des Datenspeichers, oder der Program Counter weitergegeben wird
###### Beispiel
![[Pasted image 20221209133934.png]]