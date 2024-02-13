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
#### Stack Canary
- Die Stack Canary ist ein zufaelliger Wert, der vor der Ruecksprungadresse abgespeichert wird
- Vor einem Return wird der momentane Canary Wert mit dem urspruenglichen Verglichen, um Bufferoverflows zu erkennen
###### Problem
- Die Stack Canary kann umgangen werden, falls beispielsweise der Stack ausgelesen werden kann
#### Data Execution Prevention
- Seiten werden als nicht-ausfuehrbar markiert, um das Ausfuehren von Code auf dem Stack zu verhindern
###### Problem
- Code Reuse, sowie Return Oriented Programming werden hierdurch nicht verhindert
#### Adress Space Layout Randomization
- Bei jedem Programmstart werden Stack- und Heapadressen randomisiert
- Mit Erweiterungen, wie PIE kann auch die Adresse des Text Segments randomisiert werden
###### Problem
- Dies bietet keinen garantierten Schutz sondern erschwert lediglich das Ausnutzen von Bufferoverflows
## Festplattenschutz
- Um Daten auf einer Festplatte abseits des Betriebssystems zu schuetzen, werden sie Verschluesselt
#### Verschluesselungsverfahren
- Ueber den AES-XTS Modus wird die Sektornummer in die Verschluesselung einbezogen
- Somit wird die Mustererkennung verhindert, ohne, dass Abhaengigkeiten zu vorherigen Bloecken entstehen
###### Schluesselverwaltung
- Da der Schluessel nicht auf der Festplatte gespeichert werden darf, muss er beim Boot eingegeben werden
## Secure Programming
- Haeufige Programmierfehler koennen durch das Befolgen von Guidelines, durch Code-Reviews oder Sanitizer vermieden werden