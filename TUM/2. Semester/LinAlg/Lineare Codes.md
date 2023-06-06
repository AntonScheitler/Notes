## Datenuebertragung
- Ein Strom aus Bits wird ueber einen gestoerten Kanal uebertragen
- Ein Infomationswort wird ueber das Hinzufuegen von Redundanz zu einem Codewort umgewandelt
- Ueber diese Redundanz koennen Fehler erkannt und korrigiert werden
#### Generatormatrizen
- Mithilfe einer [[Matrizen|Generatormatrix]] $G$ kann ein Informationswort in ein Codewort uebersetzt werden
- Hierdurch koennen Woerter mehrfach wiederholt und Paritaetsbits eingefuegt werden
- Eine Generatormatrix $G$ wird ueber $E_k \in \mathbb{K}^{k \times k}$ und $A \in \mathbb{K}^{n - k \times k}$ wie folgt konstruiert:
$$G = \begin{pmatrix}
E_k \\
A
\end{pmatrix}$$
#### Codewoerter
- Die Menge aller Codewoerter $C$ kann mithilfe der Generatormatrix $G$ beschrieben werden, wobei $k$ die Laenge der Informations- und $n$ die Laenge der Codewoerter ist:
$$C = \{ Gx \mid x \in \mathbb{K}^k\} \leq \mathbb{K}^n$$
- $C$ ist somit das Bild von $G$, wobei fuer die [[Vektorraeume|Dimension]] von $C$ und den [[Lineare Gleichungssysteme|Rang]] von $G$ gilt:
$$dim(C) = k$$
$$rg(G) = k$$
#### Dekodieren
- Ist $G$ eine Generatormatrix, $x$ ein Informationswort und $c$ das entsprechende Codewort, so kann mithilfe eines [[Lineare Gleichungssysteme|LGS]], $c$ zu $x$ dekodiert werden:
$$Gx = c$$
- Gibt es eine eindeutige Loesung, so wurde erfolgreich dekodiert
- Gibt es keine eindeutige Loesung, so muss ein $c' \in C$ gewaehlt werden, welches sich am wenigsten von $c$ unterscheidet
- Gibt es kein solches $c'$, so ist eine Dekodierung nicht moeglich
## Fehlerkorrigierende Codes
- Es sei $c \in \mathbb{K}^n$ ein beliebiges Codewort
- Das Hamming Gewicht $w(c)$ von wird definiert durch:
$$w(c) = | \{i \in \{1, ..., n\} \mid c_i \neq 0 \}|$$
- Ist $c' \in \mathbb{K}^n$ ein weiteres Codewort, so wird die Hamming Abstand zwischen $c$ und $c'$ definiert durch:
$$d(c, c') = |\{i \in \{1, ..., n\} \mid c_i \neq c'_i\}|$$
$$d(c, c') = w(c - c')$$
- Zudem wird der Hamming Abstand eines Codes $C$ beschrieben durch:
$$d(C) = min\{w(c) \mid c \in C \setminus \{0\}\}$$
#### Satz
- Es sei $C \leq \mathbb{K}^n$ ein beliebiger Code
- Ist $d(C) = 2e + 1$, so ist $C$ $e$-Fehler-korrigierend
- Ist $d(C) = 2e + 2$, so ist $C$ $e$-Fehler-erkennend
- Je groesser der Hamming Abstand eines Codes, desto mehr Fehler koennen erkannt und korrigiert werden
#### Kontrollmatrix
- Seien $A$ und $E_k$ die Bestandteile einer Generatormatrix $G$, so wird die entsprechende Kontrollmatrix $P$ wird definiert durch:
$$P = (-AE_{n - k})$$
$$PG = 0$$
- Fuer beliebige Codewoerter $c \in C$ gilt somit:
$$Pc = PGx = 0$$