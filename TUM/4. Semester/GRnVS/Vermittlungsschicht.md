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
- Unterschiedliche Teile einer IPv4 Adresse dienen dazu das Netz des Hosts, beziehungsweise den Host selbst zu identifizieren
- Die Broadcastadresse besitzt hierbei nur Einsen im Hostanteil
#### Header
- Da Router anhand der IP Adressen Weiterleitungsentscheidungen treffen, muessen die Adressen des Absenders und Emfpaengers im IP Header der Nachricht stehen
- Der IP Header enthaelt zudem zusaetzliche Informationen, wie Checksums oder die Anzahl an erlaubten Hops; der TTL
#### Adressaufloesung
- Ist nur die IP Adresse und nicht die MAC Adresse eines Geraets bekannt, so kann diese ueber eine ARP-Request im Direktverbindungsnetz in Erfahrung gebracht werden
- Wird durch die ARP-Request keine MAC gefunden, so wendet sich das Geraet an die MAC des Default Gateway, um die Nachricht in andere Netze zu versenden
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
- Dies resultiert jedoch in ineffizienter Nutzung des Adressraums und grossen Netzwerken, die unter ueberlastung leiden
- Ueber CIDR kann anhand einer Subnetzmaske die Groesse des Netz- und Hostanteils dynamisch definiert werden
###### Anwendung
- CIDR wird verwendet, um grosse Netzwerke in kleinere zu unterteilen, sowie um kleine Netzwerke in grossen zusammenzufassen
- Haeufig wird die Maske nicht angegeben, sondern stattdessen die Anzahl der fuehrenden Einsen der Maske an die IP Adresse angehaengt 
- Eine resultierende Adresse kann somit beispielsweise 192.160.0.0/23 lauten
###### Beispiel
![[Pasted image 20240605182551.png]]
## IPv6
- Da sich fuer IPv4 die Adressknappheit verbreitet, nimmt die Nutzung von IPv6 zu
- Durch IPv6 wird der Adressraum auf $2^{128}$ vergroessert und der Header vereinfacht, um ihn effizienter nutzen zu koennen
#### Header
- Der IPv6 Header enthaelt Informationen, wie die Adressen des Senders und Emfpaengers, die Laenge der Payload, sowie das Hop Limit 
- Ueber das Next Header Feld wird der Typ des Extension Headers, oder des L4 Headers bekannt gegeben
###### Extension Header
- Mithilfe von Extension Headers koennen zusaetzliche Informationen angefuegt werden