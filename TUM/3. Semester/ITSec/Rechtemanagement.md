## Modelle
- Um Zugriffsrechte zu verwalten, werden verschiedene Modelle verwendet
#### Zugriffsmatrix
- Subjekte und Objekte stellen die Zeilen und Spalten einer Matrix dar
- Eine Zelle enthaelt die Zugriffsrechte des Subjekts auf das entsprechende Object
###### Nachteile
- Die Rollen der Subjekte werden nicht betrachtet
- Die Matrix skaliert schlecht
###### Beispiel
![[Pasted image 20240119161048.png]]
#### Role-based Access Control
- Jedem Subjekt werden Rollen zugewiesen, wobei jeder Rolle eine Menge von Berechtigungen zugewiesen wird
###### Hierarchien
- Rollen und ihre Berechtigungen koennen hierarchisch angeordnet werden
###### Nachteil
- Komprimierende Informationsfluesse werden nicht reguliert
#### Bella-LaPadula Modell
- Anhand von Labels erhalten Subjekte eine Clearance und Objekte eine Classification
- Flussrelationen definieren anhand dieser Labels, welche Informationsfluesse erlaubt sind
###### BLP-MAC Policy
- Die no-read-up Regel legt fest, dass ein Subjekt nur Objekte lesen kann, deren Classification niedriger, oder gleich ihrer Clearance sind
- Die no-write-down Regel legt fest, dass ein Subjekt nur in Objekte schreiben kann, deren Classification groesser, oder gleich ihrer Clearance sind
###### Nachteil
- Subjekte koennen in Objekte schreiben, ohne sie zu lesen zu duerfen
## Zugriffskontrolle
- Greift ein Subjekt auf ein Objekt zu, so muss durch Kontrollen sichergestellt werden, dass das Subjekt autorisiert ist
#### Berechtigungskontrolle
- Bei der Berechtigungskontrolle wird sichergestellt, dass das Subjekt zum Zugriff autorisiert ist
- Ist das Subjekt autorisiert, so wird eine Berechtigungsbescheinigung ausgestellt
#### Zulaessigkeitskontrolle
- Bei der Zulaessigkeitskontrolle wird sichergestellt, dass die Berechtigungsbescheinigung eines Subjekts gueltig ist 