## Verschluesselungsverfahren
- Um eine sichere Kommunikation zu gewaehrleisten, werden verschiedene Verschluesselungsverfahren verwendet
- Die Staerke eines Verschluesselungsverfahrens sollte grundsaetzlich stets im Schluessel liegen
#### Asymmetrische Verschluesselung
- Eine beliebige Entitaet $A$ besitzt zwei Schluessel $e_A$ und $d_A$
- $e_A$ ist ein oeffentlicher Schluessel, welcher jeder anderen Entitaet bekannt ist
- Von $e_A$ verschluesselte Nachrichten koennen nur durch $A$ mit dem privaten Schluessel $d_A$ entschluesselt werden
###### Vorteil
- Kommunikation zwischen Entitaeten ist moeglich, da oeffentliche Schluessel bedenkenlos geteilt werden koennen
#### Symmetrische Verschluesselung
- Ein Klartext wird mit einfachen Verfahren entschluesselt
- Die Schluessel zur Ver- und Entschluesselung sind identisch
###### Senden von Schluesseln
- Um symmetrische Schluessel mit anderen Entitaeten zu teilen, kann ein asymmetrisches Verfahren genutzt werden
###### Vorteil
- Da die symmetrische Verschluesselung sehr einfach ist, ist sie besser zur Verschluesselung groesserer Datenmengen geeignet
###### Beispiel
![[Pasted image 20231103082629.png]]
#### Blockchiffre
- Ein Klartext wird in Bloecke fester Laenge unterteilt
- Der Ciphertext setzt sich aus den verschluesselten Bloecken zusammen
###### Schwachstellen
- Eine pure Blockchiffre laesst Mustererkennung zu und ist somit unsicher
###### Beispiel
![[Pasted image 20231103094425.png]]