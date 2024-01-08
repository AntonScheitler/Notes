## Dateien
- Um den Aufbau einer physischen Festplatte zu abstrahieren, werden Dateien verwendet
- Dateien werden mithilfe von Syscalls verwaltet
#### Dateiattribute
- Dateien enthalten eine Reihe von Metainformationen, wie Zugriffsrechte, Flags und Groesse
#### Dateitypen
- Dateien werden fuer unterschiedliche Zwecke verwendet
###### Regulaere Dateien
- Regulaere Dateien enthalten Benutzerdaten, wie Text oder Binaerdaten in einem ausfuehrbaren Format
###### Verzeichnisse
- Verzeichnisse strukturieren das Dateisystem in einer Hierarchie
###### Character Special Files
- Character Special Files modellieren I/O Geraete 
###### Block Special Files
- Block Special Files modellieren Speichergeraete wie Festplatten und USB-Speicher
#### Dateizugriff
- Eine Datei kann mit open geoeffnet, mit read gelesen und write geschrieben werden
- Die Position in einer Datei kann mithilfe von lseek veraendert werden
## Dateisystemimplementierug
- Eine physische Festplatte besteht aus einer Sequenz von Bloecken gleicher Groesse
- Diese Bloecke koennen auf unterschiedliche Arten fuer Dateien belegt werden
#### Contiguous Allocation
- Eine Datei wird als zusammenhaengende Folge von Bloecken allokiert
###### Vorteile
- Die Implementierung ist einfach und Leseoperationen sehr effizient
###### Nachteile
- Es kommt zu externer Speicherfragmentierug
###### Beispiel
![[Pasted image 20240108170521.png]]
#### Linked List Allocation
- Fuer jede Datei wird eine verkettete Liste erstellt, die die allokierten Bloecke enthaelt
- Das erste Wort in einem Block dient als Pointer naechsten Block
###### Vorteile
- Externe Fragmentierung wird verhindert
###### Nachteile
- Leseoperationen sind ineffizient
- Die Kapazitaet eines Blocks wird nicht vollstaendig ausgenutzt
###### File Allocation Table
- Alternativ koennen die Pointer auf folgende Bloecke im Hauptspeicher gespeichert werden
###### Beispiel
![[Pasted image 20240108171308.png]]