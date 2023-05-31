## Datenuebertragung
- Ein Strom aus Bits wird ueber einen gestoerten Kanal uebertragen
- Ein Infomationswort wird ueber das Hinzufuegen von Redundanz zu einem Codewort umgewandelt
- Ueber diese Redundanz koennen Fehler erkannt und korrigiert werden
#### Generatormatrizen
- Mithilfe einer [[Matrizen|Generatormatrix]] $G$ kann ein Informationswort in ein Codewort uebersetzt werden
- Hierdurch koennen Woerter mehrfach wiederholt und Paritaetsbits eingefuegt werden
#### Codewoerter
- Die Menge aller Codewoerter $C$ kann mithilfe der Generatormatrix $G$ beschrieben werden, wobei $k$ die Laenge der Informations- und $n$ die Laenge der Codewoerter ist:
$$C = \{ Gx \mid x \in \mathbb{K}^k\} \leq \mathbb{K}^n$$
- $C$ ist somit das Bild von $G$, wobei fuer die [[Vektorraeume|Dimension]] von $C$ und den [[Lineare Gleichungssysteme|Rang]] von $G$ gilt:
$$dim(C) = k$$
$$rg(G) = k$$
#### Dekodieren
- Ist $G$ eine Generatormatrix, $x$ ein Informationswort und $c$ das entsprechende Codewort, so kann mithilfe eines [[Lineare Gleichungssysteme|LGS]], $c$ zu $x$ dekodiert werden:
$$Ax = c$$
- Gibt es eine eindeutige Loesung, so wurde erfolgreich dekodiert
- Gibt es keine eindeutige Loesung, so muss ein $c' \in C$ gewaehlt werden, welches sich am wenigsten von $c$ unterscheidet
- Gibt es kein solches $c'$, so ist eine Dekodierung nicht moeglich