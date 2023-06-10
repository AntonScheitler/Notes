## Einfache Verfahren
#### Selection Sort
- Das kleinste Element der verbleibenden Eingabesequenz wird gesucht und an den Anfang der Sequenz getauscht
###### Beispiel
![[Pasted image 20230606145711.png]]
#### Insertion Sort
- Das naechste Element der verbliebenden Eingabesequenz wird entfernt und an der richtigen Stelle im sortierten Teilarray untergebracht
###### Beispiel
![[Pasted image 20230606150432.png]]
## Effizientere Verfahren
#### Merge Sort
- Die Eingabesequenz wird rekursiv aufgeteilt und sortiert zusammengefuegt
###### Beispiel
![[Pasted image 20230606151259.png]]
#### Quick Sort
- Es wird ein Element der Sequenz als Pivot gewaehlt
- Alle Elemente, die kleiner sind, als das Pivotelement werden links davon angeordnet, die, die groesser sind, rechts davon
- Das Pivotelement steht nun an der richtigen Stelle und das Verfahren wird fuer die linke und rechte Haelfte wiederholt
###### Beispiel
![[Pasted image 20230610130736.png]]
#### Radix Sort
- Die Ziffern aller Zahlen der Sequenz werden nacheinander betrachtet
- Die Zahlen werden gemaess der entsprechenden Ziffer an einem bestimmten Index in einem [[Hashing|Hash Table]] eingefuegt
- Die Elemente des Hash Tables werden in eine Sequenz umgewandelt und das Verfahren wird fuer alle Ziffern wiederholt
###### Beispiel
![[Pasted image 20230610141557.png]]
## Master Theorem
- Fuer die [[Effizienzmetrik|Effizienzmessung]] von rekursiven Programmen, wird das Master Theorem verwendet
- Es seien $a, b, c, d$ positive Konstanten und $n = b^k$ die Groesse des Problems
- Es gilt folgende Rekursionsgleichung:
$$r(n) = \begin{cases}
a & \text{falls } n = 1 \\
cn + d * r(n/b) & \text{falls } n > 1
\end{cases}$$
- $d$ ist die Anzahl der Teilprobleme, in die das Problem aufgeteilt wird und $n/b$ ist die, daraus resultierende Problemgroesse
- Fuer $r(n)$ gilt:
$$r(n) = \begin{cases}
\Theta(n) & \text{falls } d < b \\
\Theta(n \log(n)) & \text{falls } d = b \\
\Theta(n^{\log_bd}) & \text{falls } d > b
\end{cases}$$
## Rang-Selektion
- Um das k-kleinste Element in einer Sequenz zu finden, wird eine Variante von Quicksort verwendet
#### Quick Select
- Nach der Aufteilung der Sequenz mithilfe eines Pivotelements wird nurnoch der Bereich betrachtet, der das k-kleinste Element enthalten kann
- Wurde das k-kleinste Element als Pivot gewaehlt, so kann es zurueckgegeben werden
###### Beispiel
![[Pasted image 20230610142936.png]]