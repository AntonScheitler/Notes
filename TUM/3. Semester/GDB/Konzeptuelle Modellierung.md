## Entity-Relationship Modell
- Fuer den Konzeptuellen Entwurf einer Datenbank werden Entity-Relationship Modelle verwendet
#### Entities
- Verschiedene Entities stehen in Beziehungen zueinander
- Entities werden zudem mithilfe von Attributen beschrieben
- Der Schluessel ist ein Attribut, welches den Entity eindeutig definiert
###### Schwacher Entitytyp
- Alle Entities eines schwachen Typs nehmen an einer Beziehung Teil
- Der Schluessel eines schwachen Entities ergibt sich aus seinem Schluessel und dem des Entites zu dem die Beziehung besteht
###### Beispiel
![[Pasted image 20231018114626.png]]
![[Pasted image 20231018124624.png]]
#### Beziehungen
###### n-stellige Beziehungen
- Man unterscheidet 1:1, 1:n, sowie n:m Beziehungen
- Hierbei wird jeweils ausgedrueckt wieviele Entities eines Typs in einer Beziehung mit Entities eines anderen Typs stehen
###### Min-Max Beziehungen
- Bei einer Beziehung wird ausgedrueckt, an wievielen Beziehungen eine Entity mindestens und hoechstens teilnehmen kann
###### Beispiel
![[Pasted image 20231018123352.png]]
![[Pasted image 20231018123412.png]]