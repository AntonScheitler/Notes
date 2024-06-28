## Allgemeines
- Da MAC-Adressen keine logische Struktur zur Adressierung bieten und das Gruppieren von Geraeten in Subnetze nicht unterstuetzt ist, reichen Direktverbindungsnetze nicht aus
- Um die Kommunikation zwischen zwei Geraeten zu ermoeglichen, sind unterschiedliche Ansaetze moeglich
#### Leitungsvermittlung
- Bei der Leitungsvermittlung wird eine dedizierte Leitung zwischen Sender und Empfaenger reserviert, ueber die dann die Kommunikation erfolgt
###### Phasen
- Bei einer Kommunikation koennen folgende Phasen unterscheiden werden:
	- Im Verbindungsaufbau wird eine dedizierte Verbindung ueber mehrere Hops erstellt
	- Nachdem die Verbindung erstellt wurde, werden Daten ausgetauscht, wobei auf eine Adressierung weitesgehend verzichtet werden kann
	- Ist die Kommunikation beendet, so wird im Verbindungsabbau die dedizierte Verbindung wieder freigegeben
###### Vorteile
- Beim Uebertragen der Daten muessen keine Vermittlungsentscheidungen getroffen werden
###### Nachteile
- Resourcen werden aufgrund des Reservierens der Verbindung nicht optimal genutzt 
- Der Verbindungsaufbau kann sehr komplex und zeitaufwendig sein
###### Beispiel
![[Pasted image 20240531105724.png]]
#### Nachrichtenvermittlung
- Eine Nachricht wird konstruiert und mit einem Header versehen, der Informationen fuer die Adressierung enthaelt
###### Vorteile
- Es ist kein Verbindungsaufbau noetig
###### Nachteile
- Falls das Netz ueberlastet ist, muessen Nachrichten gepuffert werden
###### Beispiel
![[Pasted image 20240531160045.png]]
#### Paketvermittlung
- Eine Nachricht wird in mehrere Pakete aufgebrochen, die jeweils einen Header besitzen, der Informationen ueber die Adressierung und Reassemblierung der Nachricht enthaelt
- Diese Pakete werden unabhaengig voneinander vermittelt
###### Vorteile
- Falls das Netz ueberlastet ist, muessen nur kleine Pakete gepuffert werden
###### Nachteile
- Die Nachricht muss beim Empfaenger reassembliert werden
###### Beispiel
![[Pasted image 20240531160806.png]]
## IPv4
- Eine IPv4 Adresse dient dazu, Geraete global zu identifizieren und besteht aus 4 Bytes, welche jeweils durch einen Punkt getrennt sind
- Der vordere Teil einer IPv4 Adresse ist der Netzanteil und dient dazu, das Netz des Hosts zu identifizieren, wobei der hintere Teil, der Hostanteil, den Hosts selbst identifiziert
- Bei IPv4 erfolgt die Fragmentierung einer Nachricht beim Router, das Reassemblieren beim Empfaenger
#### Header
- Da Router anhand der IP Adressen Weiterleitungsentscheidungen treffen, muessen die Adressen des Absenders und Emfpaengers im IP Header der Nachricht stehen
- Der IP Header enthaelt zudem zusaetzliche Informationen, wie die Laenge der Nachricht oder die Anzahl an erlaubten Hops; der TTL
#### Address Resolution Protocol
- Ist nur die IP Adresse und nicht die MAC Adresse eines Geraets bekannt, so kann diese ueber eine ARP-Request in Erfahrung gebracht werden
- Eine ARP Request wird mithilfe von Broadcasts realisiert
- Wird durch die ARP-Request keine MAC gefunden, so befindet sich der Kommunikationspartner in einem anderen Netz
- Nachrichten werden in dem Fall direkt an den Default Gateway gesendet, der diese dann an andere Netze weiterleitet
#### ICMP
- Ueber das Internet Control Message Protocol dient dazu, den Sender bei auftretenden Routing Fehlern zu informieren
- Zudem werden Moeglichkeiten bereitgestellt, um die Erreichbarkeit von Hosts zu ueberpruefen und Pakete umzuleiten
###### Ping
- Bei einem Ping sendet ein Host eine Echo Request an einen anderen 
- Wird der Host nicht erreicht, da beispielsweise die Anzahl der erlaubten Hops ueberschritten wird, so wird eine ICMP Fehlermeldung an den Sender zurueckgeschickt
###### Traceroute
- Um den Pfad nachzuvollziehen, die eine Echo Request von einem Host zum anderen nimmt, wird die TTL der Request auf 1 gesetzt und mit jedem Senden um 1 erhoeht
- Jeder Knoten des Pfads sendet somit eine ICMP Fehlermeldung an den Sender
- Anhand der IP-Quelladressen der Fehlermeldungen kann der Pfad der Request bestimmt werden
#### DHCP
- Durch das Dynamic Host Configuration Protocol, kann einem Host eine IP Adresse hinzugefuegt werden
###### Ablauf
- Der Host sendet eine DHCP Discover Nachricht, auf die ein DHCP Server mit einer IP Adresse antwortet, die der Host annehmen kann
- Ueber eine DHCP Request kann der Host eine IP Adresse anfragen
- Diese Anfrage wird durch den Server angenommen, oder abgelehnt
#### Subnetting
- Traditionell werden die Groessen des Netz- und Hostanteils von IP Adressen durch Klassen vorgeschrieben 
- Dies resultiert jedoch ineffizienter Nutzung des Adressraums und grossen Netzwerken, die entweder kaum genutzt, oder stark ueberlastet sind
- Um die Groesse des Netzanteils einer Adresse dynamisch festzulegen, kann CIDR verwendet werden
###### Zusammenfassen von Subnetzen
- Um Netze zusammenfassen zu koennen, muessen alle Netze gleich gross, nebeneinander und bis auf das letzte Bit des Netzanteils identisch sein
###### Notation
- Haeufig wird die Maske nicht angegeben, sondern stattdessen die Anzahl der fuehrenden Einsen der Maske an die IP Adresse angehaengt 
- Eine resultierende Adresse kann somit beispielsweise 192.160.0.0/23 lauten
###### Beispiel
![[Pasted image 20240605182551.png]]
## IPv6
- Da fuer IPv4 Adressknappheit herrscht, wird der verfuegbare Adressraum durch IPv6 vergroessert
- Jedes Geraet besitzt insbesondere eine lokale Local Link und eine globale Global Unique Adresse
- Ausserdem erfolgt die Fragmentierung einer Nachricht direkt beim Sender und nicht beim erst Router
#### Aufbau
- IPv6 Adressen bestehen aus 8 Abschnitten zu je 2 Byte koennen somit bis zu $2^{128}$ Hosts adressieren
- Der erste Teil einer Adresse ist der Subnet Identifier und identifiziert ein Subnetz
- Der zweite Teil ist der Interface Identifier und identifiziert Hosts innerhalb eines Subnetzes
###### Notation
- Selbst bei der Nutzung von Hexadezimalzeichen, sind IPv6 Adressen unuebersichtlich lang
- In den Abschnitten werden fuehrende Nullen somit weggelassen, und die laengste, vorderste Sequenz aus mindestens zwei Abschnitten, die nur aus Nullen bestehen, wird mit :: abgekuerzt
- 2001:0db8:0000:0000:0001:0000:0000:0001 wird somit zu 2001:db8::1:0:0:1
#### Header
- Der IPv6 Header enthaelt Informationen, wie die Adressen des Senders und Emfpaengers, die Laenge der Payload, sowie das Hop Limit, enthaelt insgesamt jedoch weniger Informationen als der IPv4 Header
###### Extension Header
- Durch das Next Header Feld koennen Extension Header bekannt gemacht werden, welche Informationen ueber die Fragmentierung oder ueber das Verfahren der vierten Schicht enthalten
- Der Aufbau eines Extension Headers unterscheidet sich abhaengig von seinem Zweck
#### Multicasting
- In IPv6 werden bestimmte Praefixe verwendet, um Multicast Nachrichten zu definieren
- Diese Nachrichten werden dann in Schicht 2 Multicasts uebersetzt, indem die ersten zwei Oktette auf 33:33 und die letzten 4 Oktette auf die letzten 2 Abschnitte der IP-Adresse gesetzt werden
###### Beispiel
![[Pasted image 20240614135405.png]]
#### SLAAC
- Mithilfe der Stateless Address Autoconfiguration kann ein Geraet, ohne DHCP Server, eine IPv6 Adresse generieren
###### Generieren von Local Link Adressen
- Der Praefix der IP-Adresse ist fe80, wobei der Rest des Subnet Identifiers auf 0 gesetzt wird
- Der Interface Identifier setzt sich aus den ersten 3 Oktetten der MAC eines Geraets zusammen, gefolgt von ff:fe und den letzten 3 Oktetten der MAC
- Das vorletzte Bit des ersten Oktetts im Interface Identifier wird zudem invertiert
###### Generieren von Gloabal Unique Adressen
- Die Global Unique Adresse eines Geraets baut auf seiner Local Link Adresse auf
- Der Subnet Identifier wird hierbei lediglich durch den des lokalen Routers ersetzt
#### Neighbor Discovery Protocol
- Anstelle von ARP wird das Neighbor Discovery Protocol verwendet um die MAC zu einer gegebenen IPv6 Adresse zu bestimmen
- Das Protocol setzt sich allgemein aus einer Neighbor Solicitation und einem Neighbor Advertisement zusammen
###### Neighbor Solicitation
- Mithilfe eines Solicited Nodes IPv6 Praefixes wird aus der gegebenen IP Adresse ein IPv6 Multicast generiert, der dann in einen Schicht 2 Multicast uebersetzt wird
- Ein Extension Header fuer Neighbor Solicitation wird versendet, um die MAC Adresse des Empfaengers zu erfragen 
###### Neighbor Advertisement
- In der Antwort des Empfaengers wird ein Extension Header fuer Neighbor Advertisement verwendet, welcher unter anderem die gesuchte MAC Adresse enthaelt
###### Vorteile
- Das NDP ist im vergleich zu ARP effizienter, da Multicasts anstelle von Broadcasts verwendet werden 
## Routing
- Router verwenden verschiedene Strategien um zu entscheiden, in welches Netz Packte gesendet werden sollen
#### Statisches Routing
- Bei statischem Routing legt ein Routing Table fest, fuer welche Adressen, Nachrichten an welche Router gesendet werden sollen
###### Aufbau
- Ein Eintrag in einem Routing Table besteht aus Destination, Next Hop und Iface
	- Die Destination ist die Adresse, an die geroutet werden muss
	- Der Next Hop ist die Adresse des Routers, an den die Nachricht als Naechstes geschickt werden soll und ist 0.0.0.0, falls die Destination im lokalen Netz liegt
	- Das Iface ist das Interface, ueber das die Nachricht versendet werden soll 
###### Praezedenz
- Fuer eine gegebene Adresse wird der Eintrag im Routing Table gewaehlt, dessen Destination die Adresse am genauesten beschreibt
- Je groesser die Subnetzmaske einer Destination ist, desto weiter oben liegt der entsprechende Eintrag in der Tabelle
###### Zusammenfassen von Eintraegen
- Eintraege koennen zusammengefasst werden, falls ihre Destinations zu einem Subnetz zusammengefasst werden koennen und ihre Next Hops und Ifaces identisch sind
###### Beispiel
![[Pasted image 20240623132429.png]]
#### Dynamisches Routing
- Um dynamisch, Routinginformationen zu generieren, kann das Distanz Vektor Routing verwendet werden
###### Ablauf
- Zu Beginn sind die Routing Tabellen aller Router leer
- Die Router senden sich, ueber Updates, gegenseitig und zeitgleich ihre Routing Tabellen und erschliessen ueber den Bellman-Ford Algorithmus somit die kuerzesten Pfade zu den anderen Routern
- Dies dauert potentiell mehrere Runden
###### Triggered Updates
- Um das Finden von Pfaden zu beschleunigen, senden Router ein Update, sobald sie ihren Routing Table veraendern
- Dier fuehrt zu Beginn zu einem Burst von Updates und einer starken Belastung des Netzes
###### Count to Infinity
- Faellt ein Link in einem etablierten Netz aus, so erhoeht sich mit jedem Update die Distanz zu allen verlorenen Routern bis ins Unendliche
- Dies kann auf verschiedene Weisen adressiert werden:
	- Bei Split Horizon wird Nachbarn von denen die Route zu einem Router X gelernt wurde, keine Route nach X geschickt
	- Bei Poison Reverse wird der Fehler erkannt, sobald die Distanz zu einem Router eine gewisse Groesse ueberschritten hat
	- Bei Path Vector besteht das Update nicht nur aus Destination und Next Hop, sondern aus dem gesamten Pfad, wodurch Schleifen erkannt werden koennen
## TODO
- NAT