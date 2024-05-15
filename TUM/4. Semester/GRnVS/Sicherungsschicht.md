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
#### Beispiel
## Verbindungen
- Die Verbindungen eines Direktverbindungsnetzes haben unterschiedliche Charakteristiken und Eigenschaften
#### Charakteristiken
- Verbindungen unterscheiden sich in vielen Faktoren
###### Uebertragungsrate
- Die Uebertragungsrate $r$ einer Verbindung gibt an, wieviel Zeit benoetigt wird, um $L$ Datenbits zu uebertragen
- Die hierfuer benoetigte Zeit wird als Serialsisierungszeit $t_S$ bezeichnet
###### Ausbreitungsverzoegerung
- Abhaengig von dem Material einer Verbindung, verzoegert sich die Ausbreitung von Signalen ueber eine Strecke
- Diese Ausbreitungsverzoegerung wird beschrieben durch
$$t_P = \frac{d}{\rho c}$$
- Die Gesamtverzoegerung ergibt sich somit aus $t_S$ und $t_P$
###### Bandbreitenverzoegerungsprodukt
- Aufgrund der Ausbreitungsverzoegerung kann sich zu einem gegebenen Zeitpunkt feste eine Menge an Bits im Kanal befinden:
$$C = \frac{d}{\rho c} \cdot r$$
#### Medienzugriff
- Verschiedene Medienzugriffsverfahren erlauben das gleichzeitige Nutzen eines Kanals
- Diese Verfahren koennen entweder konkurrierend, oder geregelt verlaufen
###### Aloha Protokoll
- Jede Station kann zu einem beliebigen Zeitpunkt eine Nachricht senden
- Die Bestaetigung einer Nachricht werden auf einer anderen Frequenz verschickt, um zusaetzliche Kollisionen zu vermeiden
![[Pasted image 20240514162328.png]]
###### Slotted Aloha Protokoll
- Stationen koennen Nachrichten nur zu festen Zeitslots senden
- Dies reduziert die Kollisionswahrscheinlichkeit
![[Pasted image 20240514162347.png]]
###### Carrier Sense Multiple Access
- Es wird gewartet, bis der Kanal frei ist, bevor Nachrichten versendet werden
- Um wiederholte Kollisionen zwischen denselben Nachrichten zu vermeiden, wird ein exponential backoff angewandt
- Hierbei warten die Stationen nach dem $k$-ten Sendeversuch, $n$ Slotzeiten, bevor die Nachricht erneut gesendet wird
- $n$ wird zufaellig gewaehlt, wobei gilt:
$$n \in \{0, ...,  \text{min}(2^{k - 1}, 1023) \}$$
###### RTS/CTS
- Moechte eine Station $A$ eine Nachricht an $B$ senden, so muss zuerst ein $RTS$ an eine Basisstation gesendet werden
- Sendet diese ein $CTS$ sowohl an $A$, als auch $B$, so darf $A$ die Nachricht senden
- $B$ darf kein $RTS$ senden, bis eine Zeitspanne, die in $CTS$ definiert wird, abgelaufen ist
- Somit koennen Kollisionen verringert werden
![[Pasted image 20240514162609.png]]
###### Token Passing
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
- Im Direktverbindungsnetz der zweiten Schicht werden Knoten eindeutig ueber ihre Media Access Controll Adresse identifiziert
- Diese MAC Adresse wird durch die Netzwerkkarte eines Geraets bereits ueber den Hersteller festgelegt 
#### Fehlererkennung
- In der zweiten Schicht werden, im Gegensatz zur ersten, keine Fehler korrigiert, sondern nur erkannt und an hoehere Schichten gemeldet
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
- Ein Switch mit nur zwei Ports ist eine Bridge
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