## Serialisierbarkeit
- Historien beschrieben die Ausfuehrungsreihenfolge von Lese- und Schreibeoperationen, sowie Aborts und Commits unterschiedlicher Transaktionen
#### Konfliktoperationen
- Konfliktoperationen sind Operationen, bei denen unterschiedliche Transaktionen auf ein Objekt zugreifen und mindestens eine der Transaktionen das Objekt modifiziert
- Die Ausfuehrungsreihenfolge der Teiloperationen bei einer Konfliktoperation ist entscheidend
###### Beispiel
- Konfliktoperationen sind verschraenktes lesen und schreiben, beziehungsweise schreiben und schreiben
#### Aequivalenz von Historien
- Zwei Historien sind aequivalent, falls die Teiloperationen aller Konfliktoperationen in derselben Reihenfolge ausgefuehrt werden
###### Beispiel
![[Pasted image 20240206095020.png]]
#### Serialisierbarkeitsgraph
- In einem Serialisierbarkeitsgraph wird eine Historie mithilfe eines Graphen beschrieben
- Knoten repraesentieren hierbei Transaktionen und Katen die Konfliktoperationen zwischen ihnen
- Eine Historie ist genau dann serialisierbar, falls ihr Serialisierbarkeitsgraph azyklisch ist
## Sperren
- Um Transaktionen zu synchronisieren, werden Sperren verwendet
- Man unterscheidet hierbei X-Sperren, welche das Schreiben von Daten erlauben und S-Sperren, welche nur das Lesen von Daten erlauben
#### Zwei Phasen Sperrprotokoll
- Jedes Objekt muss gelockt werden, bevor eine Transaktion darauf zugreifen kann
- Transaktionen durchlaufen zwei Phasen, in denen sie zunaechst Sperren fuer Daten allokieren und anschliessend wieder freigeben
- Hierdurch koennen jedoch Deadlocks entstehen
###### Beispiel
![[Pasted image 20240206104138.png]]