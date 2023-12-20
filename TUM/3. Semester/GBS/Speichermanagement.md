## Adressraeume
- Um zu verhindern, dass ein [[Prozessverwaltung|Prozess]] den gesamten Hauptspeicher belegt, wird jedem Prozess ein eigener, isolierter Adressraum zugewiesen
#### Virtualisierung
- Um die Programmierung zu vereinfachen, wird ein virtueller Adressraum mit konstanten Adressen fuer einen Prozess angelegt
- Um die virtuellen Adressen in physische Adressen zu uebersetzen, werden unterschiedliche Strategien verwendet
#### Direkte Adressierung
- Virtuelle Adressen werden direkt auf physische abgebildet
- Hierdurch muessen allerdings die Adressen, die in einem Programm verwendet werden, beim Laden korrigiert werden
![[Pasted image 20231215093609.png]]
#### Basisadressierung
- Das Betriebssystem legt eine Basisadresse fuer jeden Prozess fest
- Beim Laden wird die Basisadresse auf die virtuelle Adresse aufaddiert
![[Pasted image 20231215093523.png]]
#### Segmentadressierung
- Der Speicher wird in logische Segmente unterschiedlicher Laenge aufgeteilt, die separat adressiert werden muessen
- Ein Global Descriptor Table enthaelt Informationen ueber die Basisadresse, Laenge und Zugriffsberechtigungen fuer jedes Segment
- In ein Segmentregister wird der Index von dem Segment im GDT geschrieben, das adressiert werden soll
![[Pasted image 20231215094935.png]]
###### Swapping
- Ist der Speicher voll, so koennen die Segmente eines Prozess auf die Festplatte ausgelagert werden
## Freispeicherverwaltung
- Um Speicher fuer Prozesse zu verwalten, muss dem Betriebssystem bekannt sein, welche Speicherstellen belegt und welche frei sind
#### Bitmap
- Eine Bitmap speichert den Zustand eines Speicherblocks in einem Bit
- Ist der Block besetzt, so ist das entsprechende Bit 1, andernfalls 0
- Die Laenge der Bitmap entspricht somit der Anzahl der Bloecke im Hauptspeicher
###### Nachteil
- Die Suche nach einem freien Speicherblock mit gegebener Groesse ist sehr aufwendig
- Je kleiner die Speicherbloecke, desto groesser der Speicherbedarf einer Bitmap
###### Beispiel
![[Pasted image 20231218091243.png]]
#### Verkettete Liste
- Ein Listenelement speichert die Startadresse und die Laenge von prozesszugehoerigen, beziehungsweise freien Speicherbereichen
###### Nachteil
- Das Zusammenfuegen freier Bereiche ist aufwendig
###### Beispiel
![[Pasted image 20231218092843.png]]
#### Belegungsstrategien
- Speicher fuer Prozesse kann mit unterschiedlichen Strategien allokiert werden
###### First-Fit
- Der erste, ausreichend grosse Speicherbereich wird allokiert
###### Next-Fit
- Die First-Fit Strategie wird ab dem Bereich begonnen, in dem das letzte Mal allokiert wurde
###### Best-Fit
- Der Bereich, dessen Groessenunterschied zum zu allokierenden Bereich am kleinsten ist, wird allokiert
###### Worst-Fit
- Der Bereich, dessen Groessenunterschied zum zu allokierenden Bereich am groessten ist, wird allokiert
#### Buddy Algorithmus
- $2^l$ entspricht der kleinsten moeglichen Blockgroesse, $2^u$ der Groessten
- Es werden $i$ Freispeicherlisten fuer die Groessen $2^i$ angelegt, wobei zu Beginn nur eine Freispeicherliste der Groesse $2^u$ existiert
###### Speicherbelegung
- Ein Prozess der Groesse $s$ wird allokiert
- Falls $s \leq 2^{i-1}$ ist, wird ein Block aus der Freispeicherliste fuer $2^i$ entfernt und zwei Bloecke an die Liste fuer die Groesse $2^{i-1}$ angehaengt
- Dies wird wiederholt, bis $2^{i-1} < s \leq 2^i$ gilt
- Nun kann ein Block aus der Liste fuer die Groesse $2^i$ entfernt und durch den Prozess belegt werden
###### Speicherfreigabe
- Wird ein Block der Groesse $2^i$ freigegeben, so wird er an die entsprechende Liste angehaengt
- Falls in der Liste bereits ein Block existiert, werden beide Bloecke entfernt und ein Block an die Liste fuer die Groesse $2^{i-1}$ angehaengt
###### Beispiel
![[Pasted image 20231218171210.png]]
#### Fragmentierung
- Fragmentierung tritt auf, falls Speicher so vergeben wird, dass Teile ungenutzt bleiben
###### Interne Fragmentierung
- Falls Speicher in festen Bloecken vergeben wird, kann es sein, dass ein Prozess mehr Speicher allokiert als benoetigt wird
- Der uebrige Speicher bleibt ungenutzt
###### Externe Fragmentierung
- Falls Speicher in dynamischen Groessen vergeben wird, kann es sein, dass kleine Bereiche zwischen vergebenen Bereichen ungenutzt bleiben
## Paging
- Der virtuelle Adressraum wird ein Seiten, der physische Speicher in Kacheln fester groesse aufgeteilt
#### Memory Management Unit
- Durch die MMU werden virtuelle Adressen in physische uebersetzt
###### Page Tables
- Ein Page Table speichert Informationen zur Uebersetzung von virtuellen Adressen
- Ein Eintrag in einem Page Table enthaelt Informationen ueber die physische Adresse, sowie den Zustand der Seite, wie Present, Referenced oder Dirty Bits
###### Translation Lookaside Buffer
- Da Uebersetzungen aufwendig sind, werden in TLBs haeufige Uebersetzungen gecached
###### Mehrstufiges Paging
- Da Paging hohen Speicherbedarf hat, werden Page Tables hierarchisch angeordnet und nur zum Teil in den Hauptspeicher eingelagert
- Ein Eintrag in einem Page Table referenziert den naechsten Page Table in der Hierarchie
![[Pasted image 20231218181201.png]]
#### Ein- und Auslagerung
- Ist der Speicherbedarf eines Prozess groesser, als der Hauptspeicher erlaubt, so koennen Seiten auf die Festplatte ausgelagert werden
- Falls versucht wird, auf eine Seite zuzugreifen, die nicht im Hauptspeicher liegt, kommt es zu einem Seitenfehler und die Seite muss in den Hauptspeicher eingelagert werden
###### Vorteile
- Die Granularitaet ist hierbei feiner als beim Swapping von Segmenten
#### Seitenersetzungsstrategien
- Um die Anzahl von Uebersetzungen zu verringern, muss optimal entschieden werden, welche Seiten ein- oder ausgelagert werden
###### FIFO
- Die aelteste, eingelagerte Seite wird ausgelagert
- Dies fuehrt zu Problemen, falls eine Seite lange eingelagert ist und haeufig genutzt wird
###### Second Chance
- Ist das R-Bit der aeltesten Seite gesetzt, so wird dieses geloescht und die Seite erneut in die Liste eingefuegt
- Wurde eine Seite ohne gesetztes R-Bit gefunden, so wird diese ausgelagert
###### Clock Algorithmus
- Ein Pointer referenziert die aelteste, eingelagerte Seite
- Falls das R-Bit gesetzt ist, wird es geloescht und der Pointer deutet auf die naechste Seite
- Wurde eine Seite ohne gesetztes R-Bit gefunden, so wird diese ausgelagert
###### Aging
- Jedes Zeitintervall wird der Counter einer Seite um 1 erhoeht, falls ihr R-Bit gesetzt ist
- Der Counter wird dann um 1 nach rechts geshiftet und das R-Bit auf das linkeste Bit des Zaehlers addiert
![[Pasted image 20231220151929.png]]
#### Working Sets
- Die Menge der Seiten, die ein Prozess, in einem Rechenzeitintervall $\tau$ benoetigt, ist das Working Set
- Jedes Zeitintervall $I$ werden alle Seiten betrachtet und das Working Set neu konstruiert
###### Konstruktion
- Jeder Prozess besitzt einen Zaehler $Z$, der seine Rechenzeit angibt und jede Seite einen Zaehler $Z_p$ der ihre letzte Zugriffszeit angibt
- Ist das R-Bit einer Seite gesetzt, so gehoert sie zum Working Set und das entsprechende $Z_p$ wird auf $Z$ gesetzt
- Andernfalls wird die Seite aus dem Working Set entfernt, falls $Z - Z_p > \tau$, wobei $\tau$ ein Rechenzeitintervall ist