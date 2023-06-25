## Laufzeitbestimmung
- Die Laufzeit eines Programms kann auf verschiedene Weisen bestimmt werden
#### Laufzeitzuweisung
- Einer Operation in einem Programm wird eine Laufzeit zugewiesen
- Dies dient als Basis fuer weitere Laufzeitanalysen
- Elementare Zuweisungen und Vergleiche:
$$T(\text{int i = 0;}) = O(1)$$
$$T(\text{x > y}) = O(1)$$
- Hintereinanderausfuerhrung von Befehlen:
$$T(l_1 \space \text{;} \space l_2) = T(l_1) + T(l_2)$$
- Bedingungen:
$$T(\text{if (cond) then }l_1 \text{else }l_2 = O(T(\text{cond}) + max\{T(l_1), T(l_2)\})$$
- Schleifen:
$$T(\text{for (int i = a; i < n; i++)} \space l) = O(\sum_{i = a}^{n - 1}(1 + T(l)))$$
#### Worst-case Laufzeit
- In jedem Programmschritt wird vom zeitaufwaendigsten Fall ausgegangen
- Die daraus resultierende worst-case Laufzeit ist allerdings fuer die meisten Faelle nicht realistisch
###### Beispiel
![[Pasted image 20230513180843.png]]
#### Durchschnittliche Laufzeit
- Anstelle einer worst-case analyse kann die durchschnittliche Laufzeit eines Programms bestimmt werden
###### Berechnung
- Es sei $I_n$ die Menge der Instanzen eines Algorithmus und $T(i)$ die Laufzeit fuer die Instanz $i \in I_n$
- Sind alle Instanzen gleich wahrscheinlich, so gilt fuer die Laufzeit:
$$t(n) = \frac{1}{|I_n|} \sum_{i \in I_n} T(i)$$
- Wird die Wahrscheinlichkeit einer Instanz jedoch durch $p_i$ beschrieben, so gilt fuer die Laufzeit:
$$t(n) = \sum_{i \in I_n} p_i \cdot T(i)$$
###### Beispiel
![[Pasted image 20230513180744.png]]
#### Erwartungswert
- Eine Zufallsvariable $X$ dient als Abbildung einer zufaelligen Eingabe auf eine reelle Zahl
- $W_X$ beschreibt die Menge der Werte, die $X$ annehmen kann
- Die Wahrscheinlichkeit fuer das Auftreten der reellen Zahl $x$ wird beschrieben durch $Pr[X = x]$
###### Berechnung
- Mithilfe der Zufallsvariable $X$ kann der Erwartungswert folgendermassen bestimmt werden:
$$\mathbb{E}[X] = \sum_{x \in W_X} x \cdot Pr[X = x]$$
###### Beispiel
![[Pasted image 20230513180947.png]]
![[Pasted image 20230513181015.png]]
#### Amortisierung
- In manchen Faellen werden zeiteffiziente Operationen selten von sehr zeitaufwendigen Operationen gefolgt
- In der worst case Analyse fallen die zeitaufwendigen Operationen jedoch ueberdurchschnittlich ins Gewicht
- Fuer genauere Laufzeitabschaetzung wird die Kontenmethode verwendet
- Hierbei zahlen effiziente Operationen ein und Ineffiziente heben ab
###### Vorgehen
- Fuer eine Menge von Operationen $\sigma_1, ..., \sigma_m$ wird eine Funktion $\Delta$ definiert, die das Einzahlverhalten von unterschiedlichen $\sigma$ beschreibt
- Hierbei muss gelten:
$$\sum_{i=1}^m \Delta(\sigma_i) \geq 0$$
- Die amortisierte Laufzeit $A$ fuer eine Operation $\sigma$ wird mithilfe der tatsaechlichen Laufzeit $T$ beschrieben:
$$A(\sigma) = T(\sigma) + \Delta(\sigma)$$
###### Beispiel
- Ein dynamisches Array bietet die Methoden pushBack $O(1)$, popBack $O(1)$ und reallocate $O(n)$
- $\Delta$ wird folgendermassen gewaehlt:
$$\Delta(\text{pushBack}) = 2$$
$$\Delta(\text{popBack}) = 1$$
$$\Delta(\text{reallocate}) = -n$$
- Fuer die amortisierten Laufzeiten gilt somit:
$$A(\text{pushBack}) = 1 + 2 = 3$$
$$A(\text{popBack}) = 1 + 1 = 2$$
$$A(\text{reallocate}) = n - n = 0$$