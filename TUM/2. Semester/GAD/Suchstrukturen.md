## Binaere Suchbaeume
- Ein binaerer Suchbaum ist ein Graph mit einer Wurzel, wobei jeder Knoten hoechstens zwei Kinder besitzt
- Alle Knoten des linken Teilbaums von $v$ sind kleiner als $v$ und alle Knoten des rechten Teilbaums von $v$ sind groesser als $v$
#### Externe Suchbaeume
- In den Knoten werden nur Navigationsinformationen gespeichert
- Die Nutzdaten liegen in einer externen sortierten Liste
###### Beispiel
![[Pasted image 20230625160031.png]]
#### Operationen
###### Suchen
- Das gesuchte Element wird mit jedem Knoten verglichen
- Ist das gesuchte Element kleiner als der momentane Knoten, so wird der linke Teilbaum durchsucht
- Ist das gesuchte Element groesser als der momentane Knoten, so wird der rechte Teilbaum durchsucht
###### Einfuegen
- Es wird im Baum nach dem Element gesucht, um die passende Stelle fuer dieses Element zu finden
- Wurde die Stelle gefunden, wird das Element dort eingefuegt
###### Loeschen
- Es wird im Baum nach dem Element gesucht, das geloescht werden muss
- Listenelement und ihr Vaterknoten werden geloescht
- Enthaelt nicht der geloeschte Vaterknoten, sondern ein anderer Baumknoten das geloeschte Element, so wird dieser Knoten mit dem Wert vom geloeschten Vaterknoten ueberschrieben
![[Pasted image 20230625162641.png]]
![[Pasted image 20230625162657.png]]
#### Effizienz
- Ist der Baum unbalanciert, so sind die Operationen nicht effizienter als die einer verketteten Liste
###### Beispiel
![[Pasted image 20230625163559.png]]
## AVL Baeume
- Ein AVL Baum ist ein binaerer Suchbaum, wobei die Hoehendifferenz des rechten und linken Teilbaums stets zwischen -1 und 1 liegt
#### Beispiel
![[Pasted image 20230625165358.png]]
#### Operationen
- Die Teilbaeume muessen rotiert werden, um die Balancierung des Baums zu gewaehrleisten
###### Einfachrotation
- Besitzt die Hoehendifferenz zweier Knoten dasselbe Vorzeichen, wird eine Einfachrotation ausgefuehrt
- Bei negativem Vorzeichen wird rechts, bei positivem links rotiert
![[Pasted image 20230625170958.png]]
###### Doppelrotation
- Besitzt die Hoehendifferenz zweier Knoten unterschiedliche Vorzeichen, wird eine Doppelrotation ausgefuehrt
- Ist der obere Knoten positiv, wird zuerst rechts und dann links rotiert
- Ist der obere Knoten negativ, wird zuerst links und dann rechst rotiert
![[Pasted image 20230625171754.png]]
###### Einfuegen
- Das Einfuegen eines Elements erfolgt wie in einem regulaeren Suchbaum
- Vom eingefuegten Element aus werden die Elternknoten durchlaufen
- Ist die Hoehendifferenz bei einem Knoten groesser als 1, muss rotiert werden
###### Entfernen
- Es wird im Baum nach dem Element gesucht, das entfernt werden soll
- Ist das Element ein Blatt oder hat nur ein Kind, kann es geloescht, beziehungsweise durch das Kind ersetzt werden
- Hat das Element zwei Kinder, so wird es mit dem groessten Element des linken Teilbaums vertauscht und rekursiv weitergeloescht
- Anschliessend wird der Baum, falls noetig rebalanciert
#### Effizienz
- Das Suchen, Einfuegen und Loeschen erfolgt stets in $O(log(n))$
## (a, b) Baeume
- Ein (a, b) Baum ist ein Suchbaum, wobei jeder Knoten einem sortierten Array entspricht und einen eigenen Ausgangsgrad hat
#### Voraussetzungen
- Alle Blaetter des Baums liegen in derselben Tiefe
- Fuer jeden Knotengrad $d$ ausser der Wurzel gilt, falls $a \geq 2$ und $b \geq 2a - 1$:
$$a \leq d \leq b$$
- Ein Knoten besteht aus $d - 1$ sortierten Elementen und besitzt d Kinder
- Die Elemente des $i$-ten Kindes liegen zwischen dem $i-1$-ten und $i$-ten Element des Knoten
#### Beispiel
![[Pasted image 20230630193607.png]]
#### Operationen
###### Suchen
- Das gesuchte Element wird mit den Elementen eines Knotens verglichen
- Falls noetig, wird das entsprechende Kind des Knotens durchsucht
###### Einfuegen
- Es wird nach der passenden Stelle fuer das Element im Baum gesucht und das Element dort eingefuegt
- Im Knoten darueber wird das Element als Split-Key hinzugefuegt
- Falls der Knoten hierdurch einen Rang groesser als $b$ erlangt, wird der Knoten halbiert und das Element in der Mitte wiederum in den Knoten darueber eingefuegt
![[Pasted image 20230630195544.png]]