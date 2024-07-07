## Nachrichtenuebertragung
- Durch die Transportschicht werden Daten in Segmente unterteilt und jeweils mit einem Header versehen
- Die Informationen im Header haengen von dem Protokoll der Transportschicht ab
#### User Datagram Protocol
- Bei UDP enthaelt der Header lediglich Informationen ueber den Quell- und Zielport
- Gehen Pakete somit verloren, oder erreichen den Empfaenger in der falschen Reihenfolge, so kann dies nicht korrigiert werden
- UDP besitzt somit wenig Overhead, da keine Verbindungen aufgebaut werden muessen, ist jedoch auch unsicher, da beliebige Fehler unkorrigiert bleiben
#### Transport Control Protocol
- Bei TCP enthaelt der Header neben Portinformationen auch Sequenz- und Ack Nummern, um Packete reassemblieren und Verluste korrigieren zu koennen
- Um TCP Nutzen zu koennen, muss jedoch vorher, ueber den Three-Way-Handshake, eine Verbindung zwischen Sender und Empfaenger aufgebaut werden 
#### Sliding Window Verfahren
- Ueber das Sliding Window Verfahren koennen mehrere Pakete zeitgleich versendet werden, wobei potentielle Paketverluste korrigiert werden koennen
- Eine Bestaetigung $ACK = n + 1$ gilt hierbei fuer alle Segmente mit einer Sequenznummer $SEQ \leq n$
###### Go Back N
- Es wird ein Sendefenster der Groesse $s$ bei einem Sequenznummernraum $N$ festgelegt
- Wird das $i$-te Paket nicht bestaetigt, so werden im naechsten Schritt die Pakete $i, i + 1, ..., i + (s - 1)$ verschickt
- Um das Fehlinterpretieren von wiederholten Paketen zu verhindern, muss $s \leq N - 1$ sein
![[Pasted image 20240707101814.png]]
###### Selective Repeat
- Es wird ebenfalls ein Sendefenster der Groesse $s$ bei einem Sequenznummernraum $N$ festgelegt
- Wird das $i$-te Paket nicht bestaetigt, so wird davon ausgegangen, dass die uebrigen Pakete angekommen sind
- Der Sender sendet somit das $i$-te Paket, sowie das $i + (s - 1)$-te Paket nach
- Um das Fehlinterpretieren von wiederholten Paketen zu verhindern, muss hierbei $s \leq \left \lfloor \frac{N}{2} \right \rfloor$ sein
![[Pasted image 20240707102131.png]]
#### Fluss- und Staukontrolle
- Durch die Flusskontrolle wird verhindert, dass ein Empfaenger ueberlastet wird, indem er eine maximale Groesse des Sendefensters vorgibt
- Durch die Staukontrolle wird verhindert, dass ein Netz ueberlastet wird, indem der Sender Engpaesse erkennt und die Groesse des Sendefensters entsprechend anpasst
###### Staukontrolle
- Ein Staukontrollfenster reguliert die Groesse des Sendefensters 
- In der Slow Start Phase wird die Groesse des Staukontrollfensters fuer jedes bestaetigte Segment erhoeht
- In der Congestion Avoidance wird die Groesse des Staukontrollfensters nur erhoeht, falls alle gesendeten Segmente bestaetigt wurden 
- Kommt es zu Paketverlusten, so kann das Staukontrollfenster heruntergesetzt werden
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