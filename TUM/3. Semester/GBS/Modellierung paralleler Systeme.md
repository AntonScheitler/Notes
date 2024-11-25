## Petri Netze
- Parallele Systeme koennen mit einem Petri Netz modelliert werden
- Der Kontrollfluss eines parallelen Systems wird durch Tokens repraesentiert, die das Netz durchlaufen
#### Aufbau
- Ein Petri Netz setzt sich aus Stellen, Transitionen und Flussrelationen zusammen
- Stellen und Transitionen dienen als Konten und Flussrelationen als Kanten in einem Graph
###### Stellen
- Werden als Kreise modelliert und repraesentieren passive Elemente
- Stellen besitzen eine Kapazitaet, welche beschreibt, wieviele Tokens aufgenommen werden koennen
###### Transitionen
- Werden als Rechtecke modelliert und repraesentieren aktive Elemente
###### Flussrelationen
- Werden als Kanten modelliert und verbinden Stellen mit Transitionen
- Flussrelationen besitzen Gewichte, welche angeben, wieviele Transitionen ueber sie transportiert werden
#### Schalten
- Der Zustand eines Petri Netzes aendert sich durch das Schalten der Transitionen
- Eine Transition schaltet, falls die Anzahl der Tokens in den eingehenden Stellen mindestens so hoch ist wie das Gewicht der entsprechenden Flussrelation
- Zusaetzlich darf durch das Schalten der Transition die Kapazitaet der ausgehenden Stellen nicht ueberschritten werden
###### Beispiel
![[Pasted image 20231128164152.png]]
#### Erreichbarkeit
- Mithilfe eines Erreichbarkeitsgraphen werden alle moeglichen Zustaende notiert, die ein Petri Netz annehmen kann
- Ob ein gegebener Zustand erreichbar ist, kann mithilfe eines Erreichbarkeitsgraphen ueberprueft werden
###### Beispiel
![[Pasted image 20231128164922.png]]
#### Nebenlaeufigkeit
- Transitionen koennen unabhaengig voneinander schalten
- Hierdurch kann es zu Konflikten kommen
###### Beispiel
![[Pasted image 20231128164552.png]]
#### Lebendigkeit
- Ein Petri Netz ist lebendig, falls jeder Zustand von jedem anderen Zustand erreicht werden kann
- Eine Verklemmung, ist ein Zustand, in dem keine Transition schalten kann