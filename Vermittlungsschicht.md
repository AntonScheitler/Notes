## Allgemeines
- Da MAC-Adressen keine logische Struktur zur Adressierung bieten und das Gruppieren von Geraeten in Subnetze nicht unterstuetzt ist, reichen Direktverbindungsnetze nicht aus
- Ueber die Vermittlungsschicht werden unterschiedliche Direktverbindungsnetze gekoppelt und Geraete koennen global adressiert werden
## Vermittlungsarten
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
## Adressierung
- Um Kommunikation, unabhaengig von Endianness, zu ermoeglichen, wird als Network Byte Order Big Endian festgelegt
#### IPv4
- Eine IPv4 Adresse dient dazu, Geraete global zu identifizieren und besteht aus 4 Bytes, welche jeweils durch einen Punkt getrennt sind
- Das letzte Byte identifiziert das Geraet innerhalb eines Netzes
- Die ersten drei Bytes identifizieren das Netz des Geraets selbst
###### Header
- Da Router anhand der IP Adressen Weiterleitungsentscheidungen treffen, muessen die Adressen des Absenders und Emfpaengers im IP Header der Nachricht stehen
###### Adressaufloesung
- Ist nur die IP Adresse und nicht die MAC Adresse eines Geraets bekannt, so kann diese ueber eine ARP-Request im Direktverbindungsnetz in Erfahrung gebracht werden
- Wird durch die ARP-Request keine MAC gefunden, so wendet sich das Geraet an die MAC des Default Gateway, um die Nachricht in andere Netze zu versenden
#### ICMP
- Ueber das Internet Control Message Protocol dient dazu, den Sender bei auftretenden Routing Fehlern zu informieren
- Zudem werden Moeglichkeiten bereitgestellt, um die Erreichbarkeit von Hosts zu ueberpruefen und Pakete umzuleiten