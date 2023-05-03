## Effizienzmetrik
- Man betrachtet die Menge der Instanzen, die ein Algorithmus fuer ein gegebenes Problem annehmen kann
- Diese Instanzen werden nach der Groesse der Eingabe gruppiert
- Innerhalb dieser Menge an Instanzen unterscheidet man das Maximum, Minimum und den Durchschnitt anhand der Laufzeit
#### Wachstumsraten
- Es seien $f(n)$ und $g(n)$ beliebige Funktionen
- Die Funktionen haben dieselbe Wachstumsrate, falls ihr Verhaeltnis $\frac{f(n)}{g(n)}$ durch Konstanten beschraenkt ist
- Geht das Verhaeltnis $\frac{f(n)}{g(n)}$ gegen 0, so waechst $g(n)$ schneller als $f(n)$
###### Beispiel
![[Pasted image 20230425143802.png]]
#### Asymptotische Notation
- Das asymptotische Verhalten einer Funktion $f$ kann auf unterschiedliche Weisen durch eine Funktionsmenge beschrieben werden 
- Konstante Faktoren werden bei dieser Notation nicht beachtet
###### Funktionsmengen
- Menge an Funktionen, die hoechstens so schnell wachsen wie $f$:
$$O(f(n)) = \{g(n) | \space \exists c > 0 \space \exists n_0 > 0 \space \forall n \geq n_0 : g(n) \leq c \cdot f(n) \}$$
- Menge an Funktionen, die mindestens so schnell wachsen wie $f$:
$$\Omega(f(n)) = \{g(n) | \space \exists c > 0 \space \exists n_0 > 0 \space \forall n \geq n_0 : g(n) \geq c \cdot f(n) \}$$
- Menge an Funktionen, die genauso schnell wachsen wie $f$:
$$\Theta(f(n)) = \{g(n) | \space \exists c > 0 \space \exists n_0 > 0 \space \forall n \geq n_0 : g(n) = c \cdot f(n) \}$$
#### Rechenregeln
- Fuer die Laufzeit zweier Funktionen $f(n)$ und $g(n)$ gilt:
$$O(f(n)) + O(g(n)) = O(f(n) + g(n))$$
$$O(f(n)) \cdot O(g(n)) = O(f(n) \cdot g(n))$$
#### Wachstumsrate von Polynomen
- Es sei $p(n)$ ein beliebiges Polynom mit $p = \sum_{i=0}^k a_i \cdot n^i$
- Fuer dieses $p(n)$ gilt $p(n) \in O(n^k)$
## Laufzeitanalyse
- Unterschiedlichen Operationen werden verschiedene Laufzeiten zugewiesen
#### Laufzeitzuweisung
- Elementare Zuweisungen und Vergleiche:
$$T(\text{int i = 0;}) = O(1)$$
$$T(\text{x > y}) = O(1)$$
- Hintereinanderausfuerhrung von Befehlen:
$$T(l_1 \space \text{;} \space l_2) = T(l_1) + T(l_2)$$
- Bedingungen:
$$T(\text{if (cond) then }l_1 \text{else }l_2 = O(T(\text{cond}) + max\{T(l_1), T(l_2)\})$$
- Schleifen:
$$T(\text{for (int i = a; i < n; i++)} \space l) = O(\sum_{i = a}^{b - 1}(1 + T(l)))$$
#### Worst-case Laufzeit
- Zu jedem Programmschritt wird der zeitintensivste, moegliche Fall betrachtet
#### Durchschnittliche Laufzeit
- Anstelle einer worst-case analyse kann die durchschnittliche Laufzeit eines Programms bestimmt werden