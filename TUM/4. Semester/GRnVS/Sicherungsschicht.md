## Allgemeines
- In der Sicherungsschicht werden Direktverbindungsnetze verwaltet
- In diesen Netzen sind alle Knoten direkt und ohne Routing erreichbar
#### Medienzugriffe
- In einem Direktverbindungsnetz fuehren zeitgleiche Nachrichten zu Kollisionen und dem Verlust der Nachrichten
- Durch die Sicherungsschicht werden diese Kollisionen vermieden
#### Fehlerueberpruefung
- Abseits von Kanalstoerungen kann es bei der Nachrichtenuebertragung zu Fehlern kommen
- Diese Fehler muessen an hoehere Schichten weitergegeben werden
#### Adressierung
- Nachrichten koennen von mehreren Knoten empfangen werden, selbst wenn sie nicht als Empfaenger bestimmt sind  
- Dies wird durch die Sicherungsschicht vermieden
## Verbindungen
- Die Verbindungen eines Direktverbindungsnetzes haben unterschiedliche Charakteristiken und Eigenschaften
###### Uebertragungsrate
- Die Uebertragungsrate $r$ einer Verbindung gibt an, wieviel Zeit benoetigt wird, um $L$ Datenbits zu uebertragen
- Die hierfuer benoetigte Zeit wird als Serialsisierungszeit $t_S = \frac{L}{r}$ bezeichnet
###### Ausbreitungsverzoegerung
- Abhaengig von dem Material einer Verbindung, verzoegert sich die Ausbreitung von Signalen ueber eine Strecke
- Diese Ausbreitungsverzoegerung ueber einen Kanal der Laenge $d$ wird beschrieben durch:
$$t_P = \frac{d}{\rho c}$$
- Die Gesamtverzoegerung ergibt sich somit aus $t_S$ und $t_P$
###### Bandbreitenverzoegerungsprodukt
- Aufgrund der Ausbreitungsverzoegerung kann sich zu einem gegebenen Zeitpunkt feste eine Menge an Bits im Kanal befinden:
$$C = \frac{d}{\rho c} \cdot r$$
## Medienzugriff
- Verschiedene Medienzugriffsverfahren erlauben das gleichzeitige Nutzen eines Kanals
- Diese Verfahren koennen entweder konkurrierend, oder geregelt verlaufen
#### Aloha Protokoll
- Jede Station kann zu einem beliebigen Zeitpunkt eine Nachricht senden
- Die Bestaetigung einer Nachricht werden auf einer anderen Frequenz verschickt, um zusaetzliche Kollisionen zu vermeiden
- Bleibt die Bestaetigung aus, so gab es eine Kollision
###### Beispiel
![[Pasted image 20240514162328.png]]
#### Slotted Aloha Protokoll
- Stationen koennen Nachrichten nur zu festen Zeitslots senden
- Dies reduziert die Kollisionswahrscheinlichkeit
###### Beispiel
![[Pasted image 20240514162347.png]]
#### Carrier Sense Multiple Access
- Es wird gewartet, bis der Kanal frei ist, bevor Nachrichten versendet werden
- CSMA Verfahren unterscheiden sich in ihrer Persistenz:
	- Bei $1$-persistentem CSMA wird direkt gesendet, sobald der Kanal frei, ist, was zu Kollisionen fuehren kann
	- Bei $p$-persistentem CSMA wird mit einer Wahrscheinlichkeit von $p$ die Nachricht versendet und mit einer Wahrscheinlichkeit von $p - 1$ ein bestimmtes Zeitintervall gewartet, wobei die Latenz mit kleineren $p$ steigt
#### CSMA/CD
- Bemerkt eine Station waehren dem Senden ihrer Nachricht, dass es zu einer Kollision gekommen ist, so unterbricht sie ihre Nachricht und sendet stattdessen ein JAM-Signal
- Ueber dieses JAM-Signal wird andere Stationen mitgeteilt, dass ihre Nachrichten kollidiert sind
- Eine Station muss waehrend dem Senden das JAM-Signal empfangen, um benachrichtigt zu werden
- Somit muessen Nachrichten eine gewisse Mindestlaenge besitzen:
$$L_{min} = \frac{2d}{\rho c}r$$
- Da bei CSMA/CD Kollisionen erkannt werden koennen, wird auf Bestaetigungen von Nachrichten verzichtet
###### Beispiel
![[Pasted image 20240527103256.png]]
#### CSMA/CA
- Da in Funknetzwerken CSMA/CD nicht funktioniert, muessen Kollisionen stattdessem im Vorhinein vermieden werden
- Hierbei waehlt jede Station, nachdem der Kanal fuer eine gewisse Zeit frei war, zufaellig eine Menge von Backoff-Slots, die dann gewartet werden
- Erst nachdem die Backoff-Slots in einem Contention Window abgewartet wurden, und der Kanal frei ist, kann gesendet werden
###### Beispiel
![[Pasted image 20240527105422.png]]
#### RTS/CTS
- RTS/CTS ist eine Erweiterung von CSMA/CA
- Moechte eine Station $A$ eine Nachricht an $B$ senden, so muss zuerst ein $RTS$ an eine Basisstation gesendet werden
- Sendet diese ein $CTS$ sowohl an $A$, als auch $B$, so darf $A$ die Nachricht senden
- $B$ darf kein $RTS$ senden, bis eine Zeitspanne, die in $CTS$ definiert wird, abgelaufen ist
- Somit koennen Kollisionen verringert werden
###### Beispiel
![[Pasted image 20240514162609.png]]
#### Binary Exponential Backoff
- Um wiederholte Kollisionen zwischen denselben Nachrichten bei CSMA zu vermeiden, wird ein exponential backoff angewandt
- Hierbei warten die Stationen nach dem $k$-ten Sendeversuch, $n$ Slotzeiten, bevor die Nachricht erneut gesendet wird
- $n$ wird zufaellig gewaehlt, wobei gilt:
$$n \in \{0, ...,  \text{min}(2^{k - 1}, 1023) \}$$
#### Token Passing
- Alle Stationen werden in einem logischen Ring verbunden, in dem genau ein Token zirkuliert
- Moechte eine Station senden, so beansprucht sie den Token und darf als einzige im Ring, Nachrichten verschicken
- Wurden alle Nachrichten versandt, so wird der Token wieder freigegeben
- Gesendete Nachrichten zirkulieren ebenfalls im Ring und werden entfernt, sobald sie ihn einmal durchlaufen haben 
## Nachrichtenaufbau
- In der Sicherungsschicht werden Nachrichten oft als Rahmen bezeichnet
- Um Nachrichten zu unterscheiden und Uebertragungsfehler zu korrigieren, muss ihr Aufbau bestimmte Anforderungen
#### Rahmengrenzen
- Verschiedene Ansaetze koennen verwendet werden, um das Unterschieden und Abgrenzen unterschiedlicher Rahmen zu ermoeglichen
###### Laengenangaben
- Geht den Nutzdaten eine Laengenangabe voraus, so koennen Rahmen unterschieden werden 
- Der Beginn eines Rahmens kann hierbei beispielsweise durch Steuerzeichen erkannt werden
###### Steuerzeichen
- Besondere Bitsequenzen werden verwendet, um den Start und das Ende eines Rahmens zu markieren
- Das Auftreten von Steuerzeichen in den Nutzdaten kann durch zusaetzliche Kodierung, oder Character Escaping verhindert werden
###### Coderegelverletzung
- Die Regeln eines Leitungscodes werden absichtlich verletzt, um ein neues, ungueltiges Symbol zu erzeugen
- Dieses Symbol kann nun genutzt werden, um den Beginn, oder das Ende eines Rahmens zu markieren
#### Adressierung
- Im Direktverbindungsnetz der zweiten Schicht werden Knoten eindeutig ueber eine 6 Byte Media Access Controll Adresse identifiziert
- Diese MAC Adresse wird durch die Netzwerkkarte eines Geraets bereits ueber den Hersteller festgelegt 
#### Fehlererkennung
- In der zweiten Schicht werden, im Gegensatz zur ersten, keine Fehler korrigiert, sondern nur erkannt und an hoehere Schichten gemeldet
- Dies erfolgt ueber den Cyclic Redundancy Check
###### Vorgehen
- Ein Datenwort der Laenge $n$ kann dargestellt werden als ein Polynom der Form:
$$a(x) = \sum_{i = 0}^{n - 1} a_ix^i, \; x_i \in \{0, 1\}$$
- Die Addition zwischen Polynomen entspricht hierbei einer XOR Operation, Modulo dem Rest einer Polynomdivision
- Um eine Nachricht $m(x)$ von Grad $k$ mittels CRC zu uebertragen, wird ein Reduktionspolynom $r(x)$ von Grad $n$ benoetigt:
	1. $n$ Nullen werden an $m(x)$ angehaengt, sodass $m'(x) = m(x) \cdot x^n$
	2. Die Pruefsumme $c(x) = m'(x) \mod{r(x)}$ wird gebildet
	3. Die Nachricht $s(x) = m'(x) + c(x)$ wird versendet
	4. Um Uebertragungsfehler der Nachricht $s'(x) = s(x) + e(x)$ zu erkennen, prueft der Empfaenger $s'(x) \mod{r(x)} = m'(x) + c(x) + e(x) \mod{r(x)} = e(x) \mod{r(x)} \stackrel{?}{=} 0$
- Ist $s'(x) \mod{r(x)} = 0$, so kam es mit hoher Wahrscheinlichkeit zu keinem Bitfehler
- Ist $e(x)$ jedoch ein Vielfaches des Reduktionspolynoms, so wird der Fehler nicht erkannt
## Verbindungen
- Um Knoten zu einem Direkverbindungsnetz zu verbinden, werden unterschiedliche Konstrukte genutzt
#### Hubs
- Ein Hub verbindet Knoten zu einer Collision-Domain, in der die Nachrichten eines Knoten an alle anderen weitergeleitet werden
- Somit kann nur ein Knoten in der Domain gleichzeitig senden
- Innerhalb eines Hubs muessen dieselben Medienzugriffsverfahren genutzt werden
###### Beispiel
![[Pasted image 20240515124638.png]]
#### Switches
- Ein Switch verbindet, ueber seine Ports, mehrere Hubs zu einem groesseren Netzwerk und unterbrechen somit ihre Collision-Domain
- Switches merken sich auf welchem Port eine Nachricht emfpangen wurde, um dem Port die MAC Adressen der Geraete zuzuteilen, die an ihn angeschlossen sind
- Eine Bridge ist eine Art Switch, welcher nur zwischen zwei Seiten unterscheidet
- Switches koennen zudem Domaenen mit unterschiedlichen Medienzugriffsverfahren verbinden
###### Switching-Table
- Die MAC Adressen der Geraete und ihr entsprechende Port sind in einem Switching-Table vermerkt
- Hat der Empfaenger einer Nachricht einen Eintrag im Switching Table, so wird die Nachricht nur an den entsprechenden Port weitergeleitet
- Ist kein Eintrag vorhanden, wird die Nachricht auf allen Ports gesendet
###### Microsegmentation
- Werden Hubs komplett durch Switches ersetzt, so spricht man von einer Microsegmentation
![[Pasted image 20240515130126.png]]
###### Beispiel
![[Pasted image 20240515125359.png]]
#### WLAN Access Points
- Um Geraete ueber WLAN mit einem Direktverbindungsnetz zu verbinden, werden WLAN Access Points verwendet
###### Funktionsweise
- Access Points verhalten sich aehnlich zu Switches, unter der Ausnahme, dass sich Geraete bei ihnen zuvor registrieren muessen, um sie zu nutzen 
- Da bei physischen Netzen nur Destination und Source Address verwendet werden, muessen bei Access Points zusaetzlich eine Receiver und Transmitter Address angegeben werden
###### Beispiel
![[Pasted image 20240515134156.png]]
![[Pasted image 20240515134351.png]]
## Nachrichtentypen
- Durch Setzen bestimmter Bits in der Transmitter oder Receiver Address koennen unterschiedliche Arten von Nachrichten definiert werden
#### Kategorien
- Eine Unicast Nachricht wird an genau eine Station gesendet, eine Multicast Nachricht an eine Gruppe von Stationen
- Ob es sich um eine Unicast oder Multicast Nachricht handelt, wird durch das niedrigste Bit des ersten Oktetts der Transmitter Address bestimmt
- Eine Broadcast Nachricht wird an alle Stationen eines Netzwerks geschicht und wird durch eine Receiver Address, die nur aus Einsen besteht, umgesetzt