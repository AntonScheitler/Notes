## Abstrakter Datentyp
- Eine Priority Queue besteht aus einer Menge von Elementen $M$
- Jedes Element $e$ besitzt hierbei einen key, welcher seiner Prioritaet entspricht
#### Operationen
- Elemente koennen der Queue hinzugefuegt werden
- Das Element mit der hoechsten Prioritaet kann abgerufen und geloescht werden
## Heaps
- Ein binaerer Heap ist ein Binaerbaum, wobei jedes Element eine Prioritaet besitzt
- Alle Ebenen des Binaerbaums sind vollstaendig, bis auf die Letzte, welche von links vervollstaendigt wird
- Die Prioritaet eines Knoten ist mindestens so hoch wie die seiner Kindknoten
- Das Element mit der hoechsten Prioritaet ist somit die Wurzel
#### Loeschen
- Die Wurzel wird mit einem Knoten aus der untersten Ebene ersetzt
- Dieser Knoten wird mit dem Kind mit der hoechsten Prioritaet so lange vertauscht, bis er an der richtigen Stelle im Heap ist
###### Beispiel
![[Pasted image 20230613200546.png]]
#### Einfuegen
- Das neue Element wird in der untersten Ebene an der linkesten freien Stelle eingefuegt
- Das Element wird so lange mit seinem Elternknoten vertauscht, bis es an der richtigen Stelle im Heap ist
###### Beispiel
![[Pasted image 20230613201002.png]]
#### Beispiel
![[Pasted image 20230613195733.png]]
## Heap Sort
- Die Elemente eines Heaps koennen sortiert geholt werden, indem die Wurzel wiederholt abgerufen und geloescht wird
#### Beispiel
![[Pasted image 20230613204223.png]]
![[Pasted image 20230613204239.png]]