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
## Binomial Heaps
- Ein Binomial Heap wird mithilfe von Binomialbaeumen konstruiert
#### Binomialbaeume
- Binomialbaeume muessen bestimmte Eigenschaften erfuellen, um einen Binomial Heap bilden zu koennen
###### Rang
- Jeder Binomialbaum hat einen Rang
- Baeume mit dem Rang $0$ besitzen ein einzelnes Element
- Baeume mit dem Rang $r$ besitzen Kinder, die Baueme mit dem Rang $r-1, r-2, ..., 0$ sind
###### Heap-Eigenschaft
- Die Prioritaet eines Knoten ist mindestens so hoch wie die seiner Kindknoten
###### Beispiel
![[Pasted image 20230621135827.png]]
#### Heap Konstruktion
- Ein Binomial Heap ist eine Liste von Binomialbaeumen, wobei es fuer jeden Rang hoechstens einen Baum geben darf
#### Heap Merge
- Zwei Heaps koennen zusammengefuegt werden, indem beide Listen schrittweise durchlaufen und bei Bedarf gemerged werden
- Ausgehend von der Merge Operation, koennen alle weiteren Operationen definiert werden
###### Einfuegen
- Eine einelementige Liste mit dem neuen Element wird erstellt
- Diese Liste wird mit dem Heap gemerged
###### Loeschen
- Das Element mit der hoechsten Prioritaet wird geloescht
- Die Liste an Kindern des geloeschten Elements wird mit dem Heap gemerged
#### Beispiel
![[Pasted image 20230621142417.png]]