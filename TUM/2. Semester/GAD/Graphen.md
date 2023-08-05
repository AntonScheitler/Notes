## Allgemeines
- Ein Graph besteht aus einer Menge von Knoten $V$ und einer Menge von Kanten $E$, welche Knoten miteinander verbinden
- Man unterscheidet zudem gerichtete und ungerichtete Kanten
- Einer Kante kann zudem ein Gewicht zugeordnet werden
#### Darstellung
- Ein Graph kann als eine Menge von Kanten, eine Adjazenzmatrix, ein Adjazenzarray oder eine Adjazenzliste dargestellt werden
###### Beispiel
![[Pasted image 20230709154840.png]]
#### Zusammenhang
- Ein ungerichteter Graph ist zusammenhaengend, wenn es von jedem Knoten einen Pfad zu jedem anderen Knoten gibt
- Ein gerichteter Graph ist stark zusammenhaengend, wenn es von jedem Knoten einen gerichteten Pfad zu jedem anderen Knoten gibt
###### Beispiel
![[Pasted image 20230709154806.png]]
## Traversierung
- Ein Graph kann auf verschiedene Weisen durchlaufen werden
#### Breitensuche
- Von dem momentanen Knoten aus werden alle Nachbarn betrachtet
- Hierdurch wird ein Spannbaum konstruiert
- Die Breitensuche kann mithilfe einer Queue realisiert werden
###### Beispiel
![[Pasted image 20230709154901.png]]
#### Tiefensuche
- Das erste Kind des momentanen Knoten wird betrachtet
- Besuchte Knoten muessen markiert werden, um mehrfaches Durchlaufen zu verhindern
- Mithilfe der Tiefensuche koennen Kreise erkannt werden
- Tiefensuche kann mithilfe eines Stacks realisiert werden
###### Beispiel
![[Pasted image 20230709154927.png]]
## Kuerzeste Wege
- Ein kuerzester Weg kann von einer Quelle zu jedem Knoten ($SSSP$), oder von jedem Knoten zu jedem anderen Knoten ermittelt werden ($APSP$)
#### Graph ohne Kantengewicht
- Die kuerzesten Wege koennen mithilfe der Breitensuche bestimmt werden
#### Gerichteter Azyklischer Graph
- Die Knoten werden topologisch sortiert
- Jedem Knoten wird hierbei erst dann eine Nummer zugewiesen, wenn jeder Vorgaenger des Knotens betrachtet wurde
- Der Graph wird in der topologischen Reihenfolge durchlaufen und fuer jeden Knoten die kleinste Distanz bestimmt
###### Effizienz
- Die kuerzesten Wege werden in $O(n + m)$ bestimmt, wobei $n$ die Anzahl der Knoten und $m$ die Anzahl der Kanten ist
###### Beispiel
![[Pasted image 20230709161949.png]]
#### Dijkstra Algorithmus
- Es wird bei einem Startknoten begonnen und die Distanz zu jedem anderen Knoten auf $\infty$ gesetzt
- Die Distanzen zu allen Nachbarknoten des Startknotens werden gesetzt und neue Knoten in die [[Priority Queues|Prioritaetswarteschlange]] eingefuegt
- Ist eine Distanz fuer einen Nachbarknoten bereits gegeben, so wird diese aktualisiert, falls die neue Distanz kuerzer ist
- Der neue Startknoten wird aus der Prioritaetswarteschlange entnommen
- Wurden alle Knoten besucht, so wurde der $SSSP$ bestimmt
###### Effizienz
- Der Algorithmus von Dijkstra laeuft in $O(m + n\log(n))$, wobei $n$ die Anzahl der Knoten und $m$ die Anzahl der Kanten ist
###### Beispiel
![[Pasted image 20230711190344.png]]
#### Bellman-Ford Algorithmus
- Gibt es $n$ Knoten in einem Graphen, so besteht jeder Pfad zwischen zwei Knoten $v$ und $w$ aus maximal $n - 1$ Kanten
- Alle Kanten des Graphen werden $n - 1$ mal durchlaufen und in jeder Iteration die Distanz zu allen Knoten aktualisiert
- Veraendert sich in einer $n$-ten Iteration die Distanz zu einem Knoten, so fuehrt ein negativer Zyklus zu ihm
- Knoten, die ueber einen negativen Zyklus erreicht werden koennen erhalten die Distanz $-\infty$
###### Effizienz
- Der Bellman-Ford Algorithmus laeuft in $O(m * n)$, wobei $n$ die Anzahl der Knoten und $m$ die Anzahl der Kanten ist
#### APSP
- Enthaelt ein Graph keine negativen Zyklen, so koennen die $APSP$ bestimmt werden
###### Floyd-Warshall Algorithmus
- Fuer jeden Knoten $v$ wird ueberprueft, ob zwei Knoten $u$ und $w$ mit einem kuerzeren Weg verknuepft werden koennen, der ueber $v$ fuehrt
###### Johnson Algorithmus
- Die Kanten eines Graphen werden so abgeaendert, dass sie stets positiv sind
- Nun kann fuer jeden Knoten der Dijkstra Algorithmus angewandt werden
## Minimaler Spannbaum
- Ein Spannbaum ist ein azyklischer Teilgraph, der alle Knoten des Graphen enthaelt
- Ein Spannbaum ist minimal, falls die Summe seiner Kantengewichte minimal ist
#### Algorithmus von Kruskal
- Der Graph wird partitioniert, sodass jeder Knoten einen eigenen Teilgraphen bildet
- Die Teilgraphen werden iterativ ueber die guenstigste Kante zusammengefuegt, die noch nicht Teil des Spannbaums ist
- Dies wird wiederholt, bis nurnoch eine Zusammenhangskomponente besteht
###### Beispiel
![[Pasted image 20230719223534.png]]
#### Algorithmus von Prim
- Ein beliebiger Knoten wird als Startknoten gewaehlt
- Der Spannbaum wird immer um den Knoten erweitert, der mit der guenstigsten Kante am Spannbaum anliegt
- Dies wird wiederholt, bis jeder Knoten teil des Spannbaums ist
###### Beispiel
![[Pasted image 20230719223923.png]]