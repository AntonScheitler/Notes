## Arithmetische Operationen
#### Addition
- Um einen Halbaddierer zu realisieren, muessen zwei Eingabebits in ein Summenbit und ein Uebertragsbit ueberfuehrt werden  
- Ein Halbaddierer kann somit mithilfe eines XOR und eines AND Gatters realisiert werden
- Um drei Eingabebits mit einem Volladdierer addieren zu koennen, muessen zwei Halbaddierer kombiniert und die Uebertragsbits verodert werden
- Mithilfe paralleler Operationen und einem Multiplexer kann die Addition optimiert werden
###### Beispiel
![[Pasted image 20221122210042.png]]
![[Pasted image 20221122210051.png]]
![[Pasted image 20221122210103.png]]
![[Pasted image 20221122210123.png]]
#### Subtraktion
- Eine Subtraktion entspricht einer Addition, wobei einer der Operanden in sein negatives Zweierkomplement ueberfuehrt wird
- Fuer die Ueberfuehrung in das Zweierkomplement koennen XOR Gatter und ein eingehendes Carry Bit verwendet werden
###### Beispiel
![[Pasted image 20221122210342.png]]
#### Multiplikation
- Eine Multiplikation mit zwei Bits entspricht einer Verundung
- Um mehrstellige Binaerzahlen zu Multiplizieren, muss der erste Operand stellenweise mit den Bits des zweiten Operanden verundet werden
- Die daraus resultierenden Zwischenergebnisse werden zum Produkt addiert
###### Optimierung ueber Carry-Save Addierer
- Bei einem Carry-Save Addierer werden Volladdierer nicht mehr ueber die Carry Bits verbunden
- Stattdessen werden Summen und Carry Bits separat berechnet und am Ende aufsummiert
- Verwendet man in einem Multiplizierer Carry-Save Addierer, so koennen Zwischenergebnisse mit den Summen und Carry Bits des vorherigen Schritts verrechnet werden
- Da die Volladdierer in jedem Schritt nun entkoppelt sind, wird die Multiplikation beschleunigt
###### Beispiel
![[Pasted image 20221128122641.png]]
![[Pasted image 20221128125755.png]]
![[Pasted image 20221128125806.png]]
## Logische Operationen
#### Multiplexer
- Ein Multiplexer waehlt ausgehend von einem Steuersignal eines seiner Eingabesignale aus und leitet es weiter
###### Beispiel
![[Pasted image 20221128132144.png]]