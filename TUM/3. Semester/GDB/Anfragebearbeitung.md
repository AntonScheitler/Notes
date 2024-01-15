## Anfrageoptimierung
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
- slkdfjlsdfj
