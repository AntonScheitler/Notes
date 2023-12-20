## Schluesselerzeugung
- Da die Sicherheit eines [[Kryptographie|kryptographischen Verfahrens]] von der Staerke des Schluessels abhaengt, muss dieser gut gewaehlt werden
#### Entropie
- Die Entropie eines Passoworts misst seinen Informationsgehalt
- Je hoeher die Entropie eines Passworts ist, desto schwerer kann es ueber brute-force bestimmt werden
- Die Entropie eines Passworts mit der Laenge $L$ aus dem Alphabet $M$ wird ermittelt durch:
$$E = log_2(|M|^L)$$
#### Zufallszahlengenerator
- Starke Schluessel besitzen eine hohe Entropie, welche mit Zufallszahlen erzielt werden kann
- Zufallszahlen duerfen nicht vorhersagbar sein und statistisch gleichviele Nullen und Einsen besitzen, ohne komprimierbar zu sein
###### Beispiel
- Eine [[Kryptographie|Blockchiffre]] im CTR Modus dient als Zufallszahlengenerator, wobei die Nonce der Seed ist 
![[Pasted image 20231121112039.png]]
## Schluesselaustausch
- Ein Schluesselaustausch zwischen allen Entitaeten ist nicht sklaierbar, weshalb effiziente Austauschverfahren noetig sind
#### Key Encapsulation Mechanism
- Ein symmetrischer Schluessel wird ueber ein asymmetrisches Verfahren verschluesselt und zwischen Entitaeten ausgetauscht
- Wird RSA verwendet und der private Schluessel einer der Entitaeten komprimiert, sind alle zukuenftigen und vergangenen versandten Schluessel unsicher
- RSA erfuellt somit nicht das Prinzip der Perfect Forward Secrecy
###### Perfect Forward Secrecy
- Perfect Foward Secrecy ist gewaehrt, falls ein komprimierter Schluessel nicht dazu fuehrt, dass vergangene versandte Schluessel unsicher werden
#### Diffie-Hellman
- Eine Primzahl $p$ und ein Generatorelement $g \in \mathbb{Z}^{\star}_p$ sind oeffentlich
- Die Entitaeten $A$ und $B$ waehlen geheime Primzahlen $a, b \in \{2, ..., p-2\}$ und senden einander die Werte $a' = g^a \mod p$ und $b' = g^b \mod p$
- $A$ und $B$ koennen somit unabhaengig voneinander das gemeinsame Secret ermitteln $\text{DH-k}_{AB} = (b')^a \mod p = (a')^b \mod p = g^{ab} \mod p$ ermitteln
- Mithilfe einer Key Derivation Function $KDF$ kann nun ein symmetrischer Schluessel generiert werden:
$$KDF(\text{DH-k}_{AB}, n) = k_{AB}$$
###### Vorteil
- Werden $a$ und $b$ in jeder Sitzung neu gewaehlt, so erfuellt Diffie-Hellman das Prinzip der Perfect Forward Secrecy
###### Beispiel
![[Pasted image 20231128105852.png]]