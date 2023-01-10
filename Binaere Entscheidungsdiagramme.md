## Aufbau
- Das Entscheidungsdiagramm ist ein Baum, wobei jeder Knoten einer Funktion entspricht, welche entweder zu 1, oder zu 0 evaluiert
- Eine Kante entspricht dem Wert, den die Funktion annimmt und verbindet sie mit einer weitern Funktion
- Blattknoten, oder Terminale, entsprechen dem Wert, zu dem die Funktion mit der gegebenen Belegung evaluiert
#### Beispiel
- TODO
## Reduktion
#### Isomorphismus
- Sind zwei Knoten isomorph, so koennen sie unter einem zusammengefasst werden
###### Beispiel
- TODO
#### Elimination
- Deuten beide ausgehende Kanten eines Knoten auf denselbsen Knoten, so kann dieser entfernt werden
###### Beispiel
- TODO
#### Shannon Zerlegung
- Eine boolsche Funktion wird in eine Funktion bestehend aus einem Literal und einer bestehend aus den Restlichen zerlegt
- Im Entscheidungsdiagramm evaluiert das einzelne Literal zu 1, beziehungsweise zu 0
- Die darauffolgende Funktion ist die aus den restlichen Literalen
- Dieser Vorgang kann rekursiv wiederholt werden, bis das Entscheidungsdiagramm konstruiert wurde
###### Beispiel
- TODO