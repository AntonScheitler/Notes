## Repraesentation von Funktionen
- Boolesche Operationen, wie AND, OR oder NOT koennen mithilfe von Schaltungen durch Gatter repraesentiert werden
- Ausgehend von diesen grundlegenden Operationen koennen komplexere logische Funktionen implementiert werden
#### Beispiel
![[Pasted image 20221122205448.png]]
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