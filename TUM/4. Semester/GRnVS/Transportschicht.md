## Network Address Translation
- Da unter IPv4 Adressen knapp sind, koennen, mithilfe von NAT, mehrere private Adressen in eine oeffentliche Adresse uebersetzt werden
- Das Uebersetzen wird durch den Local Gateway gehandhabt 
#### Ablauf
- Sendet ein Host aus dem lokalen Netz eine Anfrage an einen Host in einem anderen Netz, so faengt der Local Gateway die Anfrage ab, und leitet die Nachricht, mit sich selbst als Sender weiter
- Der Local Gateway verfuegt ueber eine Tabelle, welche IP-Adressen und ihre Ports aus dem lokalen Netzwerk, auf die Ports des Routers abbildet 
- Antworten werden ebenfalls vom Router abgefangen und, mit dem korrekten lokalen Host als Receiver, weitergeleitet
###### Beispiel
![[Pasted image 20240706201526.png]]
#### Besonderheiten
- Verwenden mehrere lokale Hosts denselben lokalen Port, waehlt der Router einen zufaelligen, neuen Port als globalen Port
- Selbst wenn ein Eintrag fuer die Kommunikation zwischen einem lokalen und einem bestimmten remote Host erzeugt wurde, koennen trotzdem beliebige Hosts den lokalen Host ueber diesen Eintrag adressieren
- Um die Erreichbarkeit eines Servers hinter einem NAT zu garantieren, kann mithilfe von Port Forwarding ein entsprechender Eintrag in der Tabelle des Routers erzeugt werden 
#### ICMP
- Da ICMP keine Portnummern verwendet, werden Eintraege stattdessen ueber die Protokollnummer und die ICMP-ID erstellt
###### Time-Exceeded
- Da ein Time-Exceeded keine ICMP-ID beinhaltet, muss stattdessen im mitgeschickten Header und der Payload nach einer ICMP-ID gesucht werden, um Programme wie Traceroute zu ermoeglichen
## TODOs
- verbindungslose/verbindungserhaltende Uebertragungen