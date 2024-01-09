## Transportsicherheit
- Der Transport von Datenpaketen in einem Netzwerk muss sicher gestaltet werden
- Diese Sicherheitsziele werden auf verschiedene Weisen realisiert
#### Transport Layer Security
- Mithilfe von TLS kann ein sicherer Kommunikationskanal zwischen zwei Entitaeten erzeugt werden
###### Handshake
- Der Client sendet eine Zufallszahl, eine Menge von Ciphersuites, die entsprechenden [[Schluesselmanagement|Diffie-Hellman]] Parameter und eine Menge von Signaturverfahren an den Server
- Der Server sendet eine Zufallszahl, eine Ciphersuite, einen Diffie-Hellman Parameter, das Zertifikat und $Sig(H(\nabla))$, sowie $HMAC(\nabla)$, verschluesselt mit $k_{SC}$
- Nun besitzen sowohl der Client, als auch der Server das shared secret und der Client versendet abschliessend $HMAC(\nabla)$, verschluesselt mit $k_{CS}$
![[Pasted image 20240109151035.png]]
#### Firewall Architekturen
- Um das Versenden und Empfangen ungewollter Nachrichten zu verhindern, werden Firewalls verwendet
- Firewalls koennen unterschiedliche Formen annehmen
###### Paketfilter
- Anhand der Headerdaten eines Pakets wird entschieden, ob es weitergeleitet wird, oder nicht
###### Deep Package Inspection
- Sowohl die Headerdaten, als auch die Payload eines Pakets werden analysiert
- Somit kann Malware blockiert werden
###### Application Layer Gateway
- Die Kommunikation wird auf Proxys in der Firewall umgeleitet
- Die Firewall hat Einblick in die Applikation und nutzt diesen Hintergrund, um Pakete besser zu filtern