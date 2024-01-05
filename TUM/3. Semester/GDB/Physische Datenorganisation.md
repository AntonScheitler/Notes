## RAID Systeme
- Die Fehlertoleranz von Daten kann mithilfe von RAID System sichergestellt werden
#### Level
- Verschiedene Level bieten verschiedene Vorteile im Bezug auf Fehlertoleranz und Datendurchsatz auf Kosten von Speicherbedarf
###### RAID 1
- Daten werden redundant ueber zwei Platten gespeichert
- Hierdurch wird zusaetzlich eine Lastverteilung beim Lesen ermoeglicht, der Speicherbedarf verdoppelt sich hierdurch jedoch
![[Pasted image 20231220184419.png]]
###### RAID 5
- Fuer jeden Block wird ein Paritaetsblock angelegt der, verxodert mit allen Bloecken ausser einem, den uebrigen Block ergibt
- Somit werden die Daten vor dem Ausfall hoechstens einer Platte gesichert
![[Pasted image 20231220184657.png]]
## B-Baeume
- B-Baeume sind balancierte Baeume und ermoeglichen Lese-, Schreib und Entfernoperationen in $O(log(n))$
#### Aufbau
- Aehnlich zu einem [[Suchstrukturen|(a, b) Baum]] besteht ein B-Baum aus Konten, die mehrere Schluesselelemente enthalten
- Alle Kinder, die links von einem Schluesselelement liegen, sind kleiner als das Element
- Alle Kinder, die rechts von einem Schluesselelement liegen, sind groesser als das Element
###### Beispiel
![[Pasted image 20231214192433.png]]
#### Axiome
- Jeder Knoten eines B-Baumes mit Grad $k$ besitzt hoechstenes $2k$ Kinder
- Jeder innere Knoten besitzt mindestens $k$ Kinder
- Die Wurzel hat mindestens $2k$ Kinder oder ist ein Blatt
- Alle Blaetter liegen in derselben Ebene
- Ein Knoten mit $k-1$ Kindern besitzt $k$ Schluesselelemente
#### Operationen
- Die Operationen werden identisch zu denen eines (a, b) Baums implementiert