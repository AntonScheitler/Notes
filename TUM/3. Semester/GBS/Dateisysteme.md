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
- Diese Bloecke werden von Dateien belegt
#### i-nodes
- Jede Datei wird durch eine i-node repraesentiert, die die Attribute der Datei, sowie die Adressen der belegten Bloecke abspeichert
- Da i-nodes eine feste Groesse besitzen, muss fuer grosse Dateien eine Hierarchie von indirect Blocks angelegt werden
- Die Groesse eines indirect Blocks entspricht der Groesse eines Blocks auf der Festplatte 
###### Beispiel
![[Pasted image 20240118095713.png]]
## Verzeichnisimplementierung
- Verzeichnise organisieren Dateien mithilfe von ihren Verzeichniseintraegen
#### Verzeichniseintrag
- Beim Oeffnen einer Datei wird ihr Pfad verwendet, um den entsprechenden Verzeichniseintrag zu finden
- Um Verzeichniseintraege anhand eines Dateinamen zu finden, wird eine Hashtabelle verwendet
- Ein Verzeichniseintrag speichert den Namen, Adressinformationen und Attribute einer Datei
###### Dateinamen
- Dateinamen haben variable Laengen und werden im Heap gespeichert
###### Adressinformationen
- Adressinformationen werden in Form der Adresse der Datei auf der Festplatte, der Nummer ihres ersten Blocks, oder der Nummer ihrer i-node gespeichert
###### Dateiattribute
- Dateiattribute werden direkt im Verzeichniseintrag, oder in der i-node gespeichert
#### Links
- Um Dateien gemeinsam zu Nutzen, werden Links verwendet
###### Hard Links
- Ein Link auf eine geteilte Datei wird erstellt, indem ihre i-node direkt referenziert wird
###### Symbolic Links
- Eine besondere Datei wird angelegt, welche als Verweis auf den Pfad der geteilten Datei dient
## Optimierungen
- Die Korrektheit und Performanz eines Dateisystems kann mit unterschiedlichen Optimierungen verbessert werden
#### Journaling
- Um das korrekte Verhalten des Dateisystems bei Crashes zu gewaehrleisten, werden Journals verwendet
- Bevor eine Folge von Operationen ausgefuehrt wird, wird sie zunaechst in ein Journal geschrieben
- Kommt es zu einem Crash, so koennen die Operationen erneut ausgefuehrt werden
###### Idempotenz
- Damit Operationen erneut ausgefuehrt werden koennen, ohne, dass es zu Fehlern kommt, muessen sie idempotent sein
#### Virtual File System
- Um die Existenz von mehreren Dateisystemen fuer den Nutzer zu abstrahieren, werden virtuelle Dateisysteme genutzt
#### Buffer-Cache
- Zuletzt gelesene Bloecke werden in einem Buffer im Hauptspeicher gecached
- Ueber 
