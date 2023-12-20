## Anfrageoptimierung
- Anfragesprachen wie [[SQL]] spezifizieren nicht, wie die Anfrage auszufuehren ist, was Raum fuer Optmierungen laesst
- Hierfuer kann das Verhalten von Operationen der [[Relationales Datenmodell|relationalen Algebra]] ausgenutzt werden
#### Optimierungen
- Projektionen und Selektionen werden in der Ausfuehrungsreihenfolge so weit nach unten propagiert, wie moeglich
- Diejenigen Joins, die die kleinsten Zwischenergebnisse liefern, werden zuerst ausgefuehrt
- Kartesische Produkte, gefolgt von Selektionen werden zu Joins zusammengefasst