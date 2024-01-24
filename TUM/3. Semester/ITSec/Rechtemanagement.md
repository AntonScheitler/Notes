## Allgemeines
- Um Informationen in einem System sicher zu verwalten, muessen Rechte vergeben werden
#### need-to-know Rechtevergabe
- Bei der need-to-know Rechtevergabe erhalten Subjekte die minimale Anzahl an Rechten, die sie benoetigen
- Rechte koennen hierbei auf unterschiedliche Arten vergeben werden
###### Discretionary Access Control
- Der Besitzer von Daten entscheidet selbst, welches Subjekt welche Rechte auf diese Daten hat
###### Role-Based Access Control
- Jedem Subjekt wird eine Rolle zugewiesen, wobei jede Rolle mit einer Menge von Rechten assoziiert ist
- Ueber eine Hierarchie von Rollen koennen zudem Rechte vererbt werden
###### Mandatory Access Control
- Eine zentrale Entitaet gibt vor, welches Subjekt welche Rechte hat
## Modelle
- Um Zugriffsrechte zu verwalten, werden verschiedene Modelle verwendet
#### Zugriffsmatrix
- Subjekte und Objekte stellen die Zeilen und Spalten einer Matrix dar
- Eine Zelle enthaelt die Zugriffsrechte des Subjekts auf das entsprechende Object
###### Nachteile
- Die Rollen der Subjekte werden nicht betrachtet
- Die Matrix skaliert schlecht
###### Beispiel
![[Pasted image 20240122132937.png]]
#### Bell-LaPadula Modell
- Anhand von Labels erhalten Subjekte eine Clearance und Objekte eine Classification
- Flussrelationen definieren anhand dieser Labels, welche Informationsfluesse erlaubt sind
###### BLP-MAC Policy
- Die no-read-up Regel legt fest, dass ein Subjekt nur Objekte lesen kann, deren Classification niedriger, oder gleich ihrer Clearance sind
- Die no-write-down Regel legt fest, dass ein Subjekt nur in Objekte schreiben kann, deren Classification groesser, oder gleich ihrer Clearance sind
###### Nachteil
- Subjekte koennen in Objekte schreiben, ohne sie zu lesen zu duerfen
## Implementierungen
- Modelle zur Rechtevergabe koennen auf unterschiedliche Weisen implementiert werden
#### Access Control Lists
- ACLs sind eine Implementierung einer Zugriffsmatrix
- Fuer jedes Objekt wird hierbei eine Liste von Subjekten und ihren Rechten auf diese Datei verwaltet
###### Nachteile
- Das Aendern von Attributen eines Subjekts ist aufwendig
#### Capabilities
- Capabilities sind eine Implementierung einer Zugriffsmatrix
- Fuer jedes Subjekt wird eine Liste von Objekten und den Rechte auf diese verwaltet
###### Nachteile
- Die Rechteruecknahme fuer Objekte ist aufwendig
## Zugriffskontrolle
- Greift ein Subjekt auf ein Objekt zu, so muss durch Kontrollen sichergestellt werden, dass das Subjekt autorisiert ist
- Beim complete-mediation Prinzip wird jeder Zugriff auf eine geschuetzte Ressource kontrolliert
#### Berechtigungskontrolle
- Bei dem Policy-Decision Point wird sichergestellt, dass das Subjekt zum Zugriff autorisiert ist
- Ist das Subjekt autorisiert, so wird eine Berechtigungsbescheinigung ausgestellt
#### Zulaessigkeitskontrolle
- Bei dem Policy-Enforcement Point wird sichergestellt, dass die Berechtigungsbescheinigung eines Subjekts gueltig ist 