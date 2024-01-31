## RAID Systeme
- Die Fehlertoleranz von Daten kann mithilfe von RAID System sichergestellt werden
#### Level
- Verschiedene Level bieten verschiedene Vorteile im Bezug auf Fehlertoleranz und Datendurchsatz auf Kosten von Speicherbedarf
###### RAID 0
- Die Datenlast wird ueber striping gleichmaessig auf mehrere Platten verteilt
![[Pasted image 20240130181520.png]]
###### RAID 1
- Daten werden mithilfe von mirroring ueber zwei Platten gespeichert
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
- Alle Blaetter liegen in derselben Ebene
- Alle Knoten, aussser der Wurzel, eines B-Baumes von Grad $k$ besitzen mindestens $k$ und hoechstens $2k$ Eintraege
- Alle Knoten, ausser den Blaettern, mit $n$ Eintraegen besitzen $n + 1$ Kinder
#### Operationen
- Die Operationen werden identisch zu denen eines (a, b) Baums implementiert
## R-Baeume
- Ein R-Baumes partitioniert eine Punktemenge durch das Aufspannen von Rechtecken
- Die Flaeche, die durch die Rechtecke aufgespannt wird, muss hierbei minimal sein
#### Aufbau
- Jeder Eintrag in einem Knoten spannt ein Rechteck auf
- Je weiter ein Knoten von der Wurzel entfernt ist, feiner ist die Granularitaet der Partitionierung 
- Alle Blaetter liegen hierbei in derselben Ebene
###### Beispiel
![[Pasted image 20240113094748.png]]
## Erweiterbares Hashing
- Beim erweiterbaren Hashing werden Elemente anhand des Praefix ihres Hashes in die Hashtabelle eingefuegt
#### Aufbau
- Ein Directory bildet Praefixe auf Buckets ab
- Jeder Bucket kann eine gewisse Anzahl an Eintraegen enthalten
- Wird die Kapazitaet eines Buckets ueberschritten, so wird der Praefix des Directories vergroessert
###### Beispiel
![[Pasted image 20240113104629.png]]
#### Lokale und Globale Tiefe
- Die globale Tiefe ist die Groesse des Praefix, der im Directory gespeichert wird 
- Die lokale Tiefe ist die Groesse des Praefix, der in einem Bucket betrachtet werden muss, um die Elemente eindeutig zu identifizieren
