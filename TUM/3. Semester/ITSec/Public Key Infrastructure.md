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
- Die Validitaet muss hierbei haeufig und regelmaessig ueberprueft werden, da Zertifikate zurueckgerufen werden koennen
###### Beispiel
![[Pasted image 20231212110134.png]]
## Kerberos
- Kerberos ist ein Single-Sign-On Protokoll, mit dem eine Entitaet $A$ ueber einen zentralen $AuC$ Zugriff auf einen Service $S$ erhaelt
- Single-Sign-Ons basieren auf Tickets $T^{A, S}$ und Authents $Authent^A$, welche folgenden Aufbau haben:
$$T^{A, S} = (S, A, addr_A, timestamp, lifetime, k_{A,S})$$
$$Authent^A = (A, addr_A, timestamp)$$
- Tickets werden mit dem Schluessel von $S$ verschluesselt
- Authents werden mit einem , von $A$ und $S$ geteilten, Schluessel verschluesselt
#### Ablauf
- Das $AuC$ ist in einen Authenticator Service $AS$ und einen Ticket Granting Service $TGS$ aufgeteilt
- Diese Services sind fuer unterschiedliche Teile des Protokolls zustaendig
###### Authentication
- $A$ generiert mithilfe eines Passworts den Schluessel $k_A$ und erzeugt eine Nonce $N1$
- $A$ schickt an den $AS$ die Nonce und den Namen des Service, mit dem sich verbunden werden soll, in diesem Fall $TGS$
- $AS$ generiert einen shared key $k_{A, TGS}$ und erstellt ein Ticket $T^{A, TGS}$
- $AS$ schickt nun an $A$ den shared key, die Nonce und den Namen des Service, mit dem sich verbunden werden soll, verschluesselt mit $k_A$ und das Ticket $T^{A, TGS}$, verschluesselt mit $k_{TGS}$
- $A$ kann somit den shared key $k_{A, TGS}$ ermitteln und die Integritaet anhand der Nonce und dem Namen des Service ueberpruefen
![[Pasted image 20231219161020.png]]
###### Ticket Granting
- $A$ erstellt einen Authent, verschluesselt diesen mit $k_{A, TGS}$ und generiert eine Nonce 
- $A$ sendet an $TGS$ das verschluesselte Ticket $T^{A, TGS}$, die Nonce, den verschluesselten Authent und den Namen des Service, mit dem sich verbunden werden soll, in diesem Fall $S$
- $TGS$ entschluesselt das Ticket $T^{A, TGS}$, verifiziert den Authent von $A$, und generiert einen shared key $k_{A,S}$ und ein Ticket $T^{A, S}$
- $TGS$ sendet nun an $A$ den shared key, die Nonce und den Namen des Service, mit dem sich verbunden werden soll, verschluesselt mit $k_{A, TGS}$ und das Ticket $T^{A, S}$ verschluesselt mit $k_S$
- $A$ kann somit den shared key $k_{A, S}$ ermitteln und die Integritaet anhand der Nonce und dem Namen des Service ueberpruefen
![[Pasted image 20231220122809.png]]
###### Sign-On
- Um $S$ zu nutzen, sendet $A$ nun das Ticket $T^{A, S}$, verschluesselt mit $k_S$ sowie ein Authent, verschluesselt mit dem shared key $k_{A, S}$ an $S$
- $S$ entschluesselt das Ticket $T^{A, S}$ und verifiziert den Authent von $A$