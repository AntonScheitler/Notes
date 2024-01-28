## Logische Optimierungen
- Anfragesprachen wie [[SQL]] spezifizieren nicht, wie die Anfrage auszufuehren ist, was Raum fuer Optmierungen laesst
#### Aequivalente Transformationen
- Die [[Relationales Datenmodell|relationale Algebra]] laesst Umformungen von Ausdruecken zu
###### Verhalten der Selektion
- Selektionen sind kommutativ und ihre konjunktiven Praedikate koennen aufgebrochen werden
- Selektionen und Projektionen koennen vertauscht werden, falls sich die Selektionen nur auf Attribute der Projektionsliste beziehen
- Selektionen sind distributiv mit Joins und Vereinigungen
- Eine Kombination aus kartesischem Produkt und Selektion kann mit einem Join zusammengefasst werden
###### Verhalten der Projektion
- Falls $A \subseteq B$ ist, so gilt:
$$\pi_A(\pi_B(R)) = \pi_A(R)$$
- Projektionen sind distributiv mit Joins, falls sich das Joinpraedikat nur auf Attribute der Projektionsliste bezieht
- Projektionen sind distributiv mit Vereinigungen
###### Verhalten von Joins und Vereinigungen
- Joins und Vereinigungen sind kommutativ
- Joins und Vereinigungen sind jeweils assoziativ
#### Optimierungen
- Projektionen und Selektionen werden in der Ausfuehrungsreihenfolge so weit nach vorne propagiert, wie moeglich
- Diejenigen Joins, die die kleinsten Zwischenergebnisse liefern, werden zuerst ausgefuehrt
- Kartesische Produkte, gefolgt von Selektionen werden zu Joins zusammengefasst
###### Beispiel
![[Pasted image 20240113103237.png]]
## Physische Optmierungen
- Anfragen koennen nicht nur durch das Umordnen von Operationen optimiert werden, sondern auch durch das Anwenden effizienterer Operationsimplementierungen
#### Merge-Join
- Sind die Relationen sortiert, so kann mithilfe zweier Pointer der Join beschleunigt werden
#### Join mit Indexstrukturen
- Besitzen die Relationen ein Indexattributen und sind zusaetzlich sortiert, so koennen Indexstrukturen, wie B-Baeume in die Relationen integriert werden
- Somit koennen Joins mit unterschiedlichen Vergleichsoperatoren besonders effizient implementiert werden
#### Hash-Join
- Hash-Joins bauen auf Hashtabellen auf und sind besonders effizient, koennen jedoch nicht fuer alle Vergleichsoperatoren verwendet werden
###### Ablauf
- Einer der beiden Join Partner wird als Build Input genutzt, der andere als Probe Input
- Mithilfe mehrerer Hashfunktionen werden die Elemente des Build Inputs partitioniert und schliesslich in Hashtabellen eingefuegt
- Die Elemente des Proble Inputs werden ebenso partitioniert und in dieselben Hashtabellen eingefuegt
- Join Partner koennen nun effizient in den Hashtabellen gefunden werden
###### Beispiel
![[Pasted image 20240125160340.png]]
## Dynamisches Programmieren
- Um ineffiziente Ausfuehrungsreihenfolgen fruehzeitig zu erkennen, wird dynamisches Programmieren eingesetzt
- Hierfuer werden Anfragen bottom-up konstruiert, wobei unterschiedliche Ausfuehrungsreihenfolgen mit unterschiedlichen Kosten ausprobiert werden
- Baut ein Schritt auf einer Teilloesung auf, die nicht optimal ist, so wird er nicht weiter betrachtet
#### Beispiel
![[Pasted image 20240128182053.png]]