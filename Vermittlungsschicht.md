## Allgemeines
- Da MAC-Adressen keine logische Struktur zur Adressierung bieten und das Gruppieren von Geraeten in Subnetze nicht unterstuetzt ist, reichen Direktverbindungsnetze nicht aus
- Ueber die Vermittlungsschicht werden unterschiedliche Direktverbindungsnetze gekoppelt und Geraete koennen global adressiert werden
## Vermittlungsarten
- Um die Kommunikation zwischen zwei Geraeten zu ermoeglichen, sind unterschiedliche Ansaetze moeglich
#### Leitungsvermittlung
- Bei der Leitungsvermittlung wird eine dedizierte Leitung zwischen Sender und Empfaenger reserviert, ueber die dann die Kommunikation erfolgt
###### Phasen
- Bei einer Kommunikation koennen folgende Phasen unterscheiden werden:
	- Im Verbindungsaufbau wird eine dedizierte Verbindung ueber mehrere Hops erstellt
	- Nachdem die Verbindung erstellt wurde, werden Daten ausgetauscht, wobei auf eine Adressierung weitesgehend verzichtet werden kann
	- Ist die Kommunikation beendet, so wird im Verbindungsabbau die dedizierte Verbindung wieder freigegeben
###### Vorteile
- Beim Uebertragen der Daten muessen keine Vermittlungsentscheidungen getroffen werden
###### Nachteile
- Resourcen werden aufgrund des Reservierens der Verbindung nicht optimal genutzt 
- Der Verbindungsaufbau kann sehr komplex und zeitaufwendig sein
###### Beispiel
![[Pasted image 20240531105724.png]]