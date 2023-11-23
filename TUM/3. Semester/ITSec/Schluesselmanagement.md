## Schluesselerzeugung
- Da die Sicherheit eines [[Kryptographie|kryptographischen Verfahrens]] von der Staerke des Schluessels abhaengt, muss dieser gut gewaehlt werden
#### Zufallszahlengenerator
- Starke Schluessel besitzen eine hohe Entropie, welche mit Zufallszahlen erzielt werden kann
- Zufallszahlen duerfen nicht vorhersagbar sein und statistisch gleichviele Nullen und Einsen besitzen
###### Beispiel
- Eine [[Kryptographie|Blockchiffre]] im CTR Modus dient als Zufallszahlengenerator, wobei die Nonce der Seed ist 
![[Pasted image 20231121112039.png]]
## Schluesselaustausch
- Ein Schluesselaustausch zwischen allen Entitaeten ist nicht sklaierbar, weshalb effiziente Austauschverfahren noetig sind
#### Key Distribution Center
- Ein Key Distribution Center dient als Zentrale fuer den Schluesselaustausch zweier Entitaeten
- Eine Entitaet $A$ besitzt einen geteilten symmetrischen Schluessel $k_A$ mit dem KDC
- Um mit der Entitaet $B$ zu kommunizieren, wird ein Schluessel $k_{AB}$ durch das KDC erzeugt