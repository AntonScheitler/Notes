## Transportsicherheit
- Der Transport von Datenpaketen in einem Netzwerk muss sicher gestaltet werden
#### Ziele
- Nutzer und Dienste muessen authentifiziert sein
- Die Integritaet und Vertraulichkeit der Verbindung muss sichergestellt werden
- Eine Methode zum [[Schluesselmanagement|Schluesselaustausch]] wird benoetigt
- TODO refactor
#### Transport Layer Security
- Die Authentifikation wird ueber X.509 [[Public Key Infrastructure|Zertifikate]] realisiert
- TLS bietet unterschiedliche Ciphersuiten, um Daten vertraulich zu versenden
- Die Datenintegritaet wird ueber ECDSA Signaturen garantiert
###### Protokollablauf
- Eine Entitaet $A$ generiert eine Zufallszahl, waehlt entsprechend [[Schluesselmanagement|Diffie Hellman]] $a$ und schickt an den Server $B$ eine Nachricht mit der Zufallszahl, $g^a$ und einer Liste von Ciphersuiten
- Der Server $B$ generiert eine Zufallszahl, waehlt entsprechend Diffie Hellman $b$ und berechnet 
- TODO