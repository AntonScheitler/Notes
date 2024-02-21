## LR Zerlegung
- Alternativ zur klassischen gaussschen Elimination kann das LGS mithilfe einer Dekomposition ermittelt werden:
	1. $A$ wird in die obere Dreiecksmatrix $R$ und die untere Dreiecksmatrix $L$ mit Einsen in der Diagonale zerlegt
	2. Das Gleichungssystem $Ly = b$ wird geloest
	3. Das Gleichungssystem $Rx = y$ wird geloest
#### Effizienz
- Die Zerlegung ist besonders effizient, falls $A$ fuer mehrere Gleichungssysteme verwendet wird
#### Aufbau
- Fuer die Struktur der Dreiecksmatrizen gilt:
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
## QR Zerlegung
- Bei der QR Zerlegung wird eine Matrix $A$ in eine Orthogonalmatrix $Q$ und eine obere Rechtecksmatrix $R$ zerlegt
- Dies wird mithilfe von Givens-Rotationen erreicht, bei denen eine Matrix wiederholt mit orthogonalen Rotationsmatrizen $G_{\varphi}$ multipliziert wird, bis das Ergebnis eine obere Rechtecksmatrix ist
- Hierbei gilt:
$$G_{\varphi} \cdot A = R \space \Leftrightarrow \space Q^{-1} \cdot A = R \space \Leftrightarrow \space A = Q\cdot R$$
- Ein Lineares Gleichungssystem kann somit geloest werden ueber:
$$Ax = b \space \Leftrightarrow \space QRx = b \space \Leftrightarrow \space Rx = Q^Tb$$
#### Givens-Rotationen
- Eine Rotationsmatrix $G_{\varphi}$ hat folgende Form:
$$\begin{pmatrix}
\cos(\varphi) & \sin(\varphi) \\
-\sin(\varphi) & \cos(\varphi) \\
\end{pmatrix} = \begin{pmatrix}
c & s \\
-s & c \\
\end{pmatrix}$$
- Um $A$ in eine obere Dreiecksmatrix umzuwandeln, muss $\varphi$ hierbei so gewaehlt werden, dass die Eintraege unterhalb der Diagonalen $0$ sind
###### Beispiel
- Es sei $A \in \mathbb{R}^{2 \times 2}$ mit:
$$A = \begin{pmatrix}
a & d \\
b & e \\
\end{pmatrix}$$
- Fuer die Rotationsmatrix $G_{\varphi}$ muss somit gelten:
$$G_{\varphi} \begin{pmatrix}a \\ b \end{pmatrix} = \begin{pmatrix}
c & s \\
-s & c \\
\end{pmatrix}\begin{pmatrix}
a \\
b
\end{pmatrix} \overset{!}{=} \begin{pmatrix}
r \\
0 \\
\end{pmatrix}$$
- Fuer $c$ und $s$ gilt somit:
$$c = \frac{a}{\sqrt{a^2 + b^2}}, \; s=\frac{b}{\sqrt{a^2 + b^2}}$$
## Pivotsuche
- Die Diagonalwerte einer Matrix werden als Pivot bezeichnet
- Um Teilungen durch 0 zu verhindern, muss sichergestellt werden, dass die Pivots einer Matrix nicht 0 sind
- Die Pivotsuche verbessert zudem die Stabilitaet des Loesen von Gleichungssystemen
#### Suchstrategien
- Ein Pivot kann auf unterschiedliche Weise ermittelt werden
###### Zeilen- und Spaltenpivotsuche
- Bei der Zeilen- oder Spaltenpivotsuche wird ein Pivot, das den Wert 0 hat, mit dem betragsmaessig groessten Element derselben Zeile, beziehungsweise Spalte vertauscht
- Die Suche wird mit einem einfachen Zeilen-, beziehungsweise Spaltentausch realisiert
###### Matrixpivotsuche
- Bei der Matrixpivotsuche werden Pivots, die den Wert 0 haben, mit den betragsmaessig groessten Elementen der Matrix vertauscht
- Die Suche wird mit einem Zeilen-, und einem Spaltentausch realisiert