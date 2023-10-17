## Angriffsklassen
- Angriffe auf Systeme koennen unterschiedliche Formen annehmen
#### Ungenuegende Eingabevalidierung
- Mithilfe besonderer Eingaben koennen Angreifer das Fehlverhalten eines Systems ausnutzen
###### Bufferoverflow
- Ein lesender oder schreibender Zugriff auf ein Datum geht ueber die Speichergrenzen dieses Datums hinaus
- Hierdurch koennen Daten anderer Programmteile, wie Ruecksprungadressen ueberschrieben werden
###### Code Injection
- Kommandos werden in eine Eingabe integriert, sodass das System diese ausfuehrt
- Somit koennen fremde Befehle mit den Privilegien des Systems ausgefuehrt werden