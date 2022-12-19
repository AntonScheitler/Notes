## Allgemeines
- In einem [[Multicycle Prozessoren|multicycle Prozessor]] bleiben manche Bestandteile des Prozessors in einem Arbeitsschritt ungenutzt
- In einem pipelined Prozessor wird ein Befehl in Arbeitsschritte unterteilt und diese Schritte parallel bearbeitet
## Architektur
#### Arbeitsschritte
- Die Abarbeitung eines Befehls wird in Fetch, Decode, Execute, Memory und Writeback unterteilt
- Um den Zustand eines Befehls zwischen den Schritten abzuspeichern, werden sowohl Daten- als auch Steuersignale am Ende eines Schritts in Flipflops gespeichert
###### Beispiel
![[Pasted image 20221219123924.png]]
#### Performanz
- Der Takt eines pipelined Prozessors entspricht dem langsamsten Arbeitsschritt
- Besteht der Prozessor aus k Pipelinestufen mit einem Takt von t, so betraegt die Laufzeit des ersten Befehls k * t
- Jeder darauffolgender Befehl hat eine Laufzeit von t
- Je mehr Instruktionen verarbeitet werden, desto hoeher ist der Speedup des pipelined Prozessors
- Der optimale Speedup entspricht der Anzahl der Pipelinestufen
###### Beispiel
![[Pasted image 20221219124929.png]]
## Pipeline-Konflikte
#### Data Hazards
###### Ursache
- Wird in einem Befehl ein Register als Operand verwendet, in welches, aufgrund von Pipelining, im vorherigen Befehl noch nicht geschrieben wurde, kommt es zu einem Data Hazard
###### Loesung
- Erkennt der Compiler einen Data Hazard, so wird die Pipeline durch die Ausfuehrung von NOPs verzoegert
- Alternativ kann die Ausfuehrungsreihenfolge der Befehle durch den Compiler abgeaendert werden
###### Beispiel
![[Pasted image 20221219130951.png]]
![[Pasted image 20221219131013.png]]
#### Control Hazards
###### Ursache
- Bei einem Sprung kann nicht vorhergesagt werden, welcher Befehl als Naechstes geholt werden soll
###### Loesung
- Es werden unabhaengig vom Ergebnis, Befehle in die Pipeline geladen
- Durch den Compiler wird bestimmt, ob die naechsten Befehle, oder die Befehle an der Sprungadresse geladen werden
- Wurden die falschen Befehle geladen, werden die Zwischenspeicher der Pipeline zurueckgesetzt
###### Beispiel
![[Pasted image 20221219132419.png]]