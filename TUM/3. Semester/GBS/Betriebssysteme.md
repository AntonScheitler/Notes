## Aufgaben
- Das Betriebssystem bietet Schnittstellen zur Hardware, wie beispielsweise das Lesen und Schreiben von Daten
- Adressraeume und CPU werden ebenfalls von dem Betriebssystem verwaltet
## Prozesse
- Ein Prozess ist ein Programm, welches ausgefuehrt wird
#### Anforderungen
- Prozesse benoetigen Ressourcen, wie CPU oder Ein- und Ausgabe, um laufen zu koennen
- Jeder Prozess besitzt einen eigenen, abgeschotteten Adressraum, welcher virtualisiert wird
- Ist ein Prozess multi-threaded, so benoetigt er zusaetzliche Register und Befehlszaehler
## Arbeitsmodi
- Das Betriebssystem bietet unterschiedliche Modi, um Sicherheit zu garantieren
- Programme laufen hauptsaechlich im Benutzermodus und koennen mithilfe von System Calls kontrolliert in den Systemmodus wechseln
- Im Systemmodus kann direkt auf Hardwareressourcen zugegriffen werden
#### Beispiel
![[Pasted image 20231023150812.png]]
## Architekturen
- Ein Betriebssystem kann auf unterschiedliche Weisen realisiert werden
#### Monolithisches System
- Das Betriebssystem umfasst eine grosse Menge an Funktionen welche alle im Systemmodus ausgefuehrt werden
- Das System wird hierdurch jedoch unuebersichtlich und schwer zu warten
###### Beispiel
![[Pasted image 20231023150752.png]]
#### Mikrokernel System
- Das Betriebssystem wird in mehrere, kleine Module aufgeteilt
- Der Mikrokern laeuft als einziges Modul im Systemmodus und verwaltet Scheduling
- Alle anderen Systemdienste laufen als Serverprozess im Benutzermodus
- Benoetigt ein Programm einen Dienst, so erfolgt die Kommunikation ueber den Mikrokern
###### Beispiel
![[Pasted image 20231023152522.png]]