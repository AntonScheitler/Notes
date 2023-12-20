## Loesungverfahren
- Das effiziente Loesen [[Lineare Gleichungssysteme|linearer Gleichungssysteme]] $Ax = b$ ist ein wichtiger Bestandteil vieler numerischer Probleme
#### Gausssches Eliminationsverfahren
- LGS koennen durch das [[Gaussches Eliminationsverfahren|gausssche Eliminationsverfahren]] exakt und mit kubischer Komplexitaet geloest werden
###### LR Dekomposition
- Alternativ zur klassischen gaussschen Elimination kann das LGS mithilfe einer Dekomposition ermittelt werden:
	1. $A$ wird in die obere Dreiecksmatrix $R$ und die untere Dreiecksmatrix $L$ mit Einsen in der Diagonale zerlegt
	2. Das Gleichungssystem $Ly = b$ wird geloest
	3. Das Gleichungssystem $Rx = y$ wird geloest
- Dies ist besonders effizient, falls $A$ fuer mehrere Gleichungssysteme verwendet wird
- Fuer die Struktur der Dreiecksmatrizen gilt hierbei
$$L = \begin{pmatrix}
1 & 0 & 0 & ... \\
x & 1 & 0 & ... \\
x & x & \ddots & \ddots \\
x & x & x & 1
\end{pmatrix}$$
$$R = \begin{pmatrix}
x & x & x & ... \\
0 & x & x & ... \\
0 & 0 & \ddots & \ddots \\
0 & 0 & 0 & x
\end{pmatrix}$$
## Pivotsuche
- Die Diagonalwerte einer Matrix werden als Pivot bezeichnet
- Um Teilungen durch 0 zu verhindern, muss sichergestellt werden, dass die Pivots einer Matrix nicht 0 sind
#### Suchstrategien
- Bei der Zeilen- oder Spaltenpivotsuche wird ein Pivot, das den Wert 0 hat, mit dem betragsmaessig groessten Element derselben Zeile, beziehungsweise Spalte vertauscht
- Bei der Matrixpivotsuche werden Pivots, die den Wert 0 haben, mit den betragsmaessig groessten Elementen der Matrix vertauscht