## Multiprogramming
- Da unterschiedliche Prozesse unterschiedliche Ressourcen benoetigen, wird ihre Ausfuehrungsreihenfolge misachtet, um die CPU Auslastung zu erhoehen
- Somit koennen CPU intensive Prozesse ausgefuehrt werden, waehrend ein anderer Prozess mit der I/O interagiert
## Strategien
- Je nach Anforderungen sind unterschiedliche Scheduling Strategien geeignet
#### Batch Systeme
- Prozesse werden anhand der Reihenfolge ihrer Erzeugung oder nach ihrer verbleibenden Laufzeit ausgefuehrt
- In First-Come-First-Served und Shortest-Job-First werden Prozesse bis zu ihrer Terminierung ausgefuehrt
- In Shortest-Remaining-Time-Next wird ein Prozess unterbrochen, falls einer mit einer kuerzeren Laufzeit erstellt wurde
#### Interaktive Systeme
- Da die Laufzeit eines Prozess vorab nicht bekannt ist, werden Prozesse abwechselnd ausgefuehrt
###### Implementierungen
- Bei Round-Robin wechseln sich Prozesse zu einem festen Zeitintervall ab
- Durch statisches Priority-Scheduling wird vorab fuer jeden Prozess eine Proritaet berechnet, wodurch Prozesse jedoch verhungern koennen
- In dynamischem Priority-Scheduling werden die Prioritaeten periodisch neu ermittelt
#### Echtzeit Systeme
- Manche Systeme muessen strikte Zeitanforderungen erfuellen
- Prozesse besitzen somit Deadlines, die erfuellt werden muessen
###### Implementierungen
- Bei einem Rate-Monotonic-System Scheduling muessen Prozesse periodisch ausgefuhert werden
- Prozesse mit der kuerzesten Periode werden priorisiert
## Multicore Scheduling
- Sind mehrere CPUs verfuegbar, so muss die Rechenlast gleichmaessig auf sie verteilt werden
#### Rechenlastverteilung
- Es werden eine globale Warteschlange, sowie separate Warteschlangen fuer jede CPU angelegt
- Ist eine CPU idle, so wird uber work stealing die Rechenlast gleichmaessig verteilt
#### Beispiel
![[Pasted image 20231116215352.png]]