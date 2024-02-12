## Fehlerklassen
- Bei der parallelen Ausfuehrung von Transaktionen koennen unterschiedliche Fehler auftreten
#### Lost Update
- Schreiben zwei Transaktionen parallel auf denselben Daten, so koennen die Aenderungen, die durch eine Transaktion herbeigefuehrt werden durch die andere Transaktion ueberschrieben werden
###### Beispiel
![[Pasted image 20240210110750.png]]
#### Abhaengigkeit von nicht-commiteten Aenderungen
- Liest eine Transaktion ein Datum, nachdem eine Andere dasselbe Datum beschrieben hat, so haengt die lesende Transaktion von einem nicht-commiteten Zustand ab
- Kommt es nun zu einem Abort in der schreibenden Transaktion, so entsteht ein Fehler
###### Beispiel
![[Pasted image 20240210111105.png]]
#### Phantomproblem
- Fuegt eine Transaktion Daten in eine Datenbank ein, waehrend eine Andere sie wiederholt liest, so kommt es zu inkonsistenten Ausgaben in der lesenden Transaktion
###### Beispiel
![[Pasted image 20240210111330.png]]
## Historien
- Historien beschreiben die Abfolge von Operationen, die von parallelen Transaktionen ausgefuehrt werden
- Da Transaktionen parallel laufen koennen, kann keine klare Reihenfolge fuer all ihre Operationen festgelegt werden
#### Modellierung
- Historien koennen als Graphen modelliert werden, wobei Elementaroperationen, wie reads, writes oder commits, durch Knoten repraesentiert werden
- Operationen, die hintereinander ausgefuehrt werden werden mit einer Kante verbunden
- Besitzt ein Knoten mehrere eingehende Kanten, so muss zunaechst jeder eingehende Knoten besucht werden
- Besitzt ein Knoten mehrere ausgehende Kanten, so koennen die entsprechenden Operationen parallel ausgefuehrt werden
###### Beispiel
![[Pasted image 20240210120339.png]]
#### Konfliktoperationen
- Es muss zwar keine klare Reihenfolge fuer alle Operationen einer Historie geben, die Reihenfolge der Konfliktoperationen muss jedoch festgelegt werden
- Greifen zwei Transaktionen auf dasselbe Datum zu und ist mindestens einer dieser Zugriffe modifizierend, so handelt es sich bei diesen Zugriffen um eine Konfliktoperation
#### Aequivalenz
- Zwei Historien sind aequivalent, falls die Reihenfolgen ihrer Konfliktoperationen identisch sind
#### Serialisierbarkeit
- Eine Historie ist serialisierbar, falls sie zu einer sequentiellen Historie, bei der Transaktionen hintereinander ausgefuehrt werden, aequivalent ist
###### Beispiel
![[Pasted image 20240210113804.png]]
![[Pasted image 20240210113814.png]]
#### Serialisierbarkeitsgraph
- Konfliktoperationen koennen mithilfe eines Serialisierbarkeitsgraphen modelliert werden
- Transaktionen werden mithilfe von Knoten repraesentiert
- Herrscht eine Konfliktoperation zwischen zwei Transaktionen so werden sie ueber eine Kante verknuepft, die bei der ausloesenden Transaktion beginnt
###### Zusammenhang mit Serialisierbarkeit
- Eine Historie ist genau dann serialisierbar, falls ihr Serialisierbarkeitsgraph azyklisch ist
###### Beispiel
![[Pasted image 20240210121748.png]]
#### Ruecksetzbarkeit
- Eine Historie ist ruecksetzbar, falls jede Transaktion abgebrochen werden kann, ohne, dass bereits commitete Transaktionen dadurch auf falschen Daten gearbeitet haben
- Eine lesende Transaktion darf somit nicht commited werden, bis alle schreibenden Transaktionen, von denen gelesen wurde commited sind 
#### Kaskadierendes Ruecksetzen
- Baut sich eine Abhaengigkeit von einer Transaktion auf, die schluessendlich abgebrochen wird, so muessen alle abhaengigen Transaktioen ebenfalls abgebrochen werden, was die Performanz des Datenbanksystems stark verschlechtert
- Dies kann verhindert werden, indem veraenderte Daten erst gelesen werden, nachdem die entsprechende Transaktion commited wurde
###### Beispiel
![[Pasted image 20240210130643.png]]
#### Striktheit
- Eine Historie ist strikt, falls eine Transaktion keine Daten liest, oder ueberschreibt, die von einer, noch aktiven, Transaktion veraendert wurden
## Sperren
- Um Transaktionen zu synchronisieren, werden Sperren verwendet
- Man unterscheidet hierbei X-Sperren, welche das Schreiben von Daten erlauben und S-Sperren, welche nur das Lesen von Daten erlauben
#### Zwei Phasen Sperrprotokoll
- Jedes Objekt muss gelockt werden, bevor eine Transaktion darauf zugreifen kann
- Transaktionen durchlaufen somit eine Wachstumsphase, in der sie zunaechst Sperren fuer Daten allokieren und anschliessend eine Schrumpfungsphase, in der sie sie wieder freigeben
- Durch das Protokoll wird garantiert, dass die resultierende Historie serialisierbar ist
###### Strenges zwei Phasen Protokoll
- Beim strengen zwei Phasen Protokoll werden Sperren bis zum Ende der Transaktion behalten und gemeinsam freigegeben
- Somit entfaellt die Schrumpfungsphase
###### Beispiel
![[Pasted image 20240210131909.png]]
#### Beispiel
![[Pasted image 20240206104138.png]]
