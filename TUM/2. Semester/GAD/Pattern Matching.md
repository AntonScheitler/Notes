## Problem
- In einem Text der Laenge $n$ wird nach einem Teilwort der Laenge $m \leq n$ gesucht
- Die Indizes dieses Teilworts muessen zurueckgegeben werden
## Knuth-Morris-Pratt Algorithmus
- Um den Suchbereich zu optimieren, wird der Rand eines Wortes verwendet
#### Rand
- Ein Wort $r$ ist der Rand eines Wortes $w$, falls $r$ sowohl Praefix, als auch Suffix von $w$ ist
- $r$ ist der eigentliche Rand, falls er der groesste moegliche Rand, nach $w$ selbst ist
#### Shifts
- Tritt ein Mismatch auf, so wird das Suchwort so weit verschoben, bis der gematchte Praefix im Suffix liegt, in dem das Mismatch aufgetreten ist
###### Beispiel
![[Pasted image 20230722205453.png]]
###### Sichere Shifts
- Es muss garantiert werden, dass bei einem Shift kein Vorkommen des Teilworts uebersprungen wird
- Hierfuer wird ein Array $borders$ erstellt, welches am Index $i$ die Laenge des eigentlichen Rands des Praefix der Laenge $i$ des Teilworts enthaelt
- Indem bei einem Mismatch an der Stelle $j$ um $j - borders[j]$ geshiftet wird, wird sichergestellt, dass erneut am fruehesten moeglichen Vorkommen des Teilworts gesucht wird
![[Pasted image 20230722215215.png]]
#### Laufzeit
- Der Algorithmus benoetigt maximal $2n + m$ Vergleiche um ein Teilwort der Laenge $m$ in einem Text der Laenge $n$ zu finden