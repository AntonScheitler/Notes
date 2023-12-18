## RAID Systeme
- Die Fehlertoleranz von Daten kann mithilfe von RAID System sichergestellt werden
- TODO
## B-Baeume
- B-Baeume sind balancierte Baeume und ermoeglichen Lese-, Schreib und Entfernoperationen in $O(log(n))$
#### Aufbau
- Aehnlich zu einem [[Suchstrukturen|(a, b) Baum]] besteht ein B-Baum aus Konten, die mehrere Schluesselelemente enthalten
- Alle Kinder, die links von einem Schluesselelement liegen, sind kleiner als das Element
- Alle Kinder, die rechts von einem Schluesselelement liegen, sind groesser als das Element
###### Beispiel
![[Pasted image 20231214192433.png]]
#### Axiome
- Jeder Knoten eines B-Baumes mit Grad $m$ besitzt hoechstenes $2m$ Kinder
- Jeder innere Knoten besitzt mindestens $m$ Kinder
- Die Wurzel hat mindestens $2m$ Kinder oder ist ein Blatt
- Alle Blaetter liegen in derselben Ebene
- Ein Knoten mit $k-1$ Kindern besitzt $k$ Schluesselelemente
#### Operationen
- Die Operationen werden identisch zu denen eines (a, b) Baums implementiert