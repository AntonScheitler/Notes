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
- $SSSP$ kann mithilfe der Breitensuche bestimmt werden
#### Gerichteter Azyklischer Graph
- Die Knoten werden topologisch sortiert
- Jedem Knoten wird hierbei erst dann eine Nummer zugewiesen, wenn jeder Vorgaenger des Knotens betrachtet wurde
- Der Graph wird in der topologischen Reihenfolge durchlaufen und fuer jeden Knoten die kleinste Distanz bestimmt
###### Beispiel
![[Pasted image 20230709161949.png]]