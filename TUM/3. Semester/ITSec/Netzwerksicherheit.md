## Transportsicherheit
- Der Transport von Datenpaketen in einem Netzwerk muss gewisse Sicherheitsziele erfuellen
- Diese Sicherheitsziele werden ueber verschiedene Protokolle realisiert
#### Ziele
- Nutzer und Dienste muessen authentifiziert sein
- Die Vertraulichkeit der Verbindung muss ueber Verschluesselung sichergestellt werden
- Die Integritaet einer Verbindung muss garantiert werden
- Eine Methode zum [[Schluesselmanagement|Schluesselaustausch]] wird benoetigt
#### Transport Layer Security
- Die Authentifikation wird ueber X.509 [[Public Key Infrastructure|Zertifikate]] realisiert
- TLS bietet unterschiedliche Ciphersuiten, um Daten vertraulich zu versenden
- Die Datenintegritaet wird ueber ECDSA Signaturen garantiert
- Der Schluesselaustausch wird ueber Diffie Hellman realisiert
###### Protokollablauf
- TODO