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
- Verschiedene Medienzugriffsverfahren erlauben das gleichzeitige Nutzen von eines Kanals
- Diese Verfahren koennen entweder konkurrierend, oder geregelt verlaufen
###### Aloha Protokoll
- Jede Station kann zu einem beliebigen Zeitpunkt eine Nachricht senden
- Die Bestaetigung einer Nachricht werden auf einer anderen Frequenz verschickt, um zusaetzliche Kollisionen zu vermeiden
###### Slotted Aloha Protokoll
- Stationen koennen Nachrichten nur zu festen Zeitslots senden
- Dies reduziert die Kollisionswahrscheinlichkeit
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