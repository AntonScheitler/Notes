## Zertifikate
- Um die Authentizitaet von Public Keys zu garantieren, werden Zertifikate benoetigt
- Das Zertifikat enthaelt eine Bescheinigung, die bestaetigt, dass ein Public Key $e_A$ tatsaechlich einer Entitaet $A$ gehoert
- Das Zertifikat wird von einem Zertifikat-Austeller [[Kryptographische Hashfunktionen|signiert]]
#### Aufbau
- Eine Registration Authority ermoeglicht die Registrierung von $A$ und ihrem Public Key $e_A$
- Die Certificate Authority erstellt das Zertifikat, welches dann von einem Directory abgerufen werden kann
###### Beispiel
![[Pasted image 20231212102909.png]]
#### Hierarchie
- Um die Authentizitaet einer Certificate Authority zu garantieren, wird eine Hierarchie von CAs konstruiert
- Eine CA besitzt mehrere uebergeordnete CAs, welche ihre Zertifikate signieren
- Eine root CA besitzt keine uebergeordnete Instanz und signiert ihre Zertifikate selbst
###### Beispiel
![[Pasted image 20231212103916.png]]
#### Validierung
- Mithilfe des Online Certificate Status Protocols kann eine Entitaet die Validitaet ihres Zertifikats ueber eine CA ueberpruefen
- Die Validitaet muss hierbei haeufig und regelmaessig ueberprueft werden
###### Beispiel
![[Pasted image 20231212110134.png]]
## Single-Sign-On
- Eine Entitaet $A$ versucht, sich mit einem Service zu verbinden
- $A$ authentisiert sich gegenueber einem AuC und fordert ein Ticket fuer den Service
- Das Ticket wird ueber den geteilten Schluessel der AuC und des Service verschluesselt und an $A$ versandt
- $A$ sendet nun das Ticket an den Service und authentisiert sich ueber einen geteilten Schluessel mit dem Service
#### Beispiel
![[Pasted image 20231212111558.png]]