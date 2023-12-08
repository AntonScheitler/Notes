## Signale
- Das Betriebssystem stellt eine Menge von Signalen zur Verfuegung, mit der Prozesse miteinander Kommunizieren koennen
- Die Kommunikation erfolgt mithilfe von Signal Handlern, die von Prozessen definiert werden
## Synchrone und Asynchrone Kommunikation
- Bei einer synchronen Kommunikation werden beide Prozesse blockiert
- Bei einer asynchronen Kommunikation werden die Prozesse voneinander entkoppelt
- Mithilfe von send und recv koennen Nachrichten verschickt und erhalten werden
#### Meldung
- Meldungen sind kurze, unidirektionale Nachrichten
###### Synchron
- Der Sender verschickt die Nachricht und blockiert, bis er eine Empfangsbestaetigung erhaelt
###### Asynchron
- Der Sender verschickt die Nachricht, ohne auf eine Bestaetigung zu warten
#### Auftrag
- Auftraege und ihre Resultate werden als Meldungen verschickt
###### Synchron
- Der Sender blockiert nachdem er den Auftrag verschickt und wird erst bei Erhalt des Resultats freigegeben
###### Asynchron
- Der sender verschickt den Auftrag und erhaelt das Resultat unabhaengig voneinander
## Kommunikationsmittel
- Um die Interprozesskommunikation zu gewaehrleisten, werden unterschiedliche Mittel benoetigt
#### Streams
- Verbindungen zwischen Prozessen werden als ein Bytestrom abstrahiert, in den der Sender schreibt und aus dem der Empfaenger liest
###### Beispiel
![[Pasted image 20231208105745.png]]
#### Pipes
- Eine Pipe ist ein unidirektionaler Kanal, ueber den Prozesse miteinander kommunizieren koennen
###### Anonyme Pipes
- Ueber den pipe syscall werden zwei Dateideskriptoren erzeugt, die die Enden einer Pipe repraesentieren
- Die Pipe existiert nur innerhalb des Programms
- Falls Kindprozesse erzeugt werden, muss sichergestellt werden, dass Lese- und Schreibzugriffe trotz zusaetzlicher Teilung der Pipe deterministisch sind
![[Pasted image 20231208180721.png]]
###### Named Pipes
- Named Pipes sind im Dateisystem verlinkt und koennen mit open geoeffnet werden
- Named Pipes bleiben auch nach Prozessende erhalten
#### Ports
- Um Kommunikation mit mehreren Prozessen, ueber den eigenen Adressraum hinweg zu ermoeglichen, werden Ports verwendet
- Ein Rechner verfuegt ueber eine feste Anzahl an Ports
- Zu einem gegebenen Zeitpunkt kann ein Port nur durch einen Prozess beansprucht werden
###### Client und Server
- Ein Server ist ein passiver Prozess, welcher auf Verbindungsanfragen auf seinem Port wartet
- Ein Client ist ein aktiver Prozess, welcher mit passiven Prozessen kommuniziert und dem hierfuer dynamisch ein Port zugewiesen wird
#### Sockets
- Eine Socket ist eine bidirektionale Verbindung zwischen zwei Ports
###### Server Socket
- Der Server erstellt mithilfe von socket eine Socket, und veroeffentlicht diese mit bind unter einer Adresse
- Ueber listen wartet der Server nun auf Clients, die eine Verbindung anfordern
- Wurde eine Verbindung angefordert, so kann ueber die Socket des Client kommuniziert werden
###### Client Socket
- Der Client erstellt mithilfe von socket eine Socket und verbindet sich ueber connect mit dem Server
- Die erstellte Socket wird nun fuer die Kommunikation mit dem Server verwendet
###### Beispiel
![[Pasted image 20231208120223.png]]
#### Software-Bussysteme
- Um Kommunikation zwischen mehreren Kommunikationspartnern zu ermoeglichen, werden Verbindungen benoetigt
- Um Kommunikationspartner effizient zu verbinden, werden Software-Bussysteme verwendet
###### Beispiel
![[Pasted image 20231208181243.png]]