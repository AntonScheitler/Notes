## Hauptspeicherschutz
- Unsichere Programmierung kann verschiedene Sicherheitsluecken auf dem Hauptspeicher ermoeglichen
#### Bufferoverflow
- Wird ein Buffer auf dem Stack gespeichert, so kann ueber einen Bufferoverflow der Stack eines Programms ueberschrieben werden
- Hierdurch kann der Stackframe mit eigenem Code ueberschrieben und die Ruecksprungadresse geaendert werden, um genau diesen Code auszufuehren
###### Beispiel
![[Pasted image 20240130103249.png]]
###### Code Reuse
- Statt den Stackframe mit Code zu ueberschreiben, wird bereits geladener Maschinencode ausgefuehrt 
###### Return Oriented Programming
- Es werden verschiedene Ruecksprungadressen und Werte auf den Stack geschrieben, wodurch verschiedene Abschnitte des urspruenglichen Programms aneinander gereiht werden koennen
- Hierdurch kann beliebiges Verhalten erzeugt werden
#### Data Execution Prevention
- Seiten werden als nicht-ausfuehrbar markiert, um das Ausfuehren von Code auf dem Stack zu verhindern
- TODO
###### Problem
- Code Reuse, sowie Return Oriented Programming werden hierdurch nicht verhindert
## Festplattenschutz
- Um Daten auf einer Festplatte abseits des Betriebssystems zu schuetzen, werden sie Verschluesselt
#### Verschluesselungsverfahren
- TODO