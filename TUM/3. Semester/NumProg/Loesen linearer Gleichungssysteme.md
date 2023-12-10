## Loesungverfahren
- Das effiziente Loesen [[Lineare Gleichungssysteme|linearer Gleichungssysteme]] $Ax = b$ ist ein wichtiger Bestandteil vieler numerischer Probleme
#### Gausssches Eliminationsverfahren
- LGS koennen durch das [[Gaussches Eliminationsverfahren|gausssche Eliminationsverfahren]] exakt und mit kubischer Komplexitaet geloest werden
###### LE Dekomposition
- Alternativ zur klassischen gaussschen Elimination kann das LGS mithilfe einer Dekomposition ermittelt werden:
	1. $A$ wird in die obere Dreiecksmatrix $R$ und die untere Dreiecksmatrix $L$ mit Einsen in der Diagonale zerlegt
	2. Das Gleichungssystem $Ly = b$ wird geloest
	3. Das Gleichungssystem $Rx = y$ wird geloest