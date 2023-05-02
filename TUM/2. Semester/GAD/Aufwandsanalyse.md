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
- Einfachen Operationen wie Zuweisungen und return statements wird die Laufzeit $O(1)$ zugewiesen
- If statements statements uebernehmen die Laufzeit des laengeren Rumpfs zuzueglich zu der Zeit, die zur Evaluation der Bedingung benoetigt wird
- Loops wird eine Laufzeit von $O(n)$ zugewiesen, wobei n die Anzahl der Elemente ist, ueber die iteriert wird
- TODO latex fuer zuweisung, if und loops
#### Durchschnittliche Laufzeit
- Anstelle einer worst-case analyse kann die durchschnittliche Laufzeit eines Programms bestimmt werden