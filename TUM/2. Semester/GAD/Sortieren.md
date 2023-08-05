## Einfache Verfahren
#### Selection Sort
- Das kleinste Element der verbleibenden Eingabesequenz wird gesucht und an den Anfang der Sequenz getauscht
###### Laufzeit
- Selection Sort laeuft in $\Theta(n^2)$
###### Beispiel
![[Pasted image 20230606145711.png]]
#### Insertion Sort
- Das naechste Element der verbliebenden Eingabesequenz wird entfernt und an der richtigen Stelle im sortierten Teilarray untergebracht
###### Laufzeit
- Insertion Sort laeuft im average case in $O(n^2)$, im best case jedoch in $\Theta(n)$
- Insertion Sort ist zudem stabil
###### Beispiel
![[Pasted image 20230606150432.png]]
## Effizientere Verfahren
#### Merge Sort
- Die Eingabesequenz wird rekursiv aufgeteilt und sortiert zusammengefuegt
###### Laufzeit
- Merge Sort laeuft stets in $O(n\log(n))$ und benoetigt $O(n)$ Speicher
- Merge Sort ist zudem stabil
###### Beispiel
![[Pasted image 20230606151259.png]]
#### Quick Sort
- Es wird ein Element der Sequenz als Pivot gewaehlt
- Alle Elemente, die kleiner sind, als das Pivotelement werden links davon angeordnet, die, die groesser sind, rechts davon
- Das Pivotelement steht nun an der richtigen Stelle und das Verfahren wird fuer die linke und rechte Haelfte wiederholt
###### Laufzeit
- Quick Sort laeuft im average case in $O(n \log n)$ und benoetigt $O(\log n)$ Speicher
- Im worst case laeuft Quick Sort in $O(n^2)$
###### Beispiel
![[Pasted image 20230610130736.png]]
#### Radix Sort
- Die Ziffern aller Zahlen der Sequenz werden nacheinander betrachtet
- Die Zahlen werden gemaess der entsprechenden Ziffer an einem bestimmten Index in einem [[Hashing|Hash Table]] eingefuegt
- Die Elemente des Hash Tables werden in eine Sequenz umgewandelt und das Verfahren wird fuer alle Ziffern wiederholt
###### Laufzeit
- Radix Sort laeuft in $\Theta(d(n + K))$ wobei $n$ die Anzahl der Elemente, $K$ das groesste Element und $d$ die Anzahl der Stellen beschreibt
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
- $a$ ist die Problemgroesse im Basisfall
- $d$ ist die Anzahl der Teilprobleme, in die das Problem aufgeteilt wird und $n/b$ ist die, daraus resultierende Problemgroesse
- $cn$ ist zudem die Problemgroesse auf der momentanen Rekursionsebene
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
## Externes Sortieren
- Datenmengen, welche nicht auf einmal in den Hauptspeicher geladen werden koennen, muessen sortiert werden
#### Vorgehen
- Der Hauptspeicher besitzt eine Groesse von $M$
- Die Daten werden stueckweise sortiert und anschliessend verschmolzen
###### Sortieren
- Daten der Groesse $M$ werden in den Hauptspeicher geladen, dort in-place sortiert und zurueckgeschrieben
###### Verschmelzen
- Es werden drei Puffer im Hauptspeicher angelegt, wobei zwei als Eingabe und einer als Ausgabe dient
- In die Eingabepuffer werden Ausschnitte von sortierten Teilfeldern geladen
- Die beiden Eingaben werden sortiert in den Ausgabepuffer uebertragen und dieser zurueckgeschrieben
#### Beispiel
![[Pasted image 20230614132021.png]]