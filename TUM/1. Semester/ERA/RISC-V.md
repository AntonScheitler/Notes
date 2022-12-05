## Befehle
- TODO
#### Befehlskodierung
- TODO
### Konstanten
- TODO
## Register
- Einem RISC-V Computer stehen 32 Register zur Verfuegung
- Jedes Register hat eine Breite von 4 Bytes
- Diese Register koennen als Speicher als temporaere Register und Ruecksprungadressen
#### Beispiel
![[Pasted image 20221205124540.png]]
## Speicher
- Der Speicherbedarf eines RISC-V Programms kann potentiell die Anzahl der Register ueberschreiten
- Zusaetzliche Daten koennen in einem separaten Speicher gehalten werden
- Da dieser Speicher nur eine Breite von einem Byte hat, nimmt ein Registerwert 4 Speicherzeilen in Anspruch
#### Speicherzugriff
###### Lesezugriff
- Von einer Speicheradresse kann ueber den lw gelesen werden
- Hierbei wird als Ziel ein Register und als Quelle eine Adresse mit einem Offset gewaehlt
- Um einen Speicherzugriff durchzufuehren, muss somit ebenfalls eine Addition erfolgen
###### Schreibzugriff
- Parallel zu lw kann mit sw ein Registerinhalt in eine Speicheradresse geschrieben werden
###### Beispiel
![[Pasted image 20221205125448.png]]
![[Pasted image 20221205125459.png]] 
#### Beispiel
![[Pasted image 20221205131215.png]]