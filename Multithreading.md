## Allgemeines
- Ein Hardware-Thread ist eine Ausfuehrungseinheit, welche aus einem Befehlszaehler und Registern besteht
- Andere Ressourcen, wie Speicher und Rechenwerke werden von Threads geteilt
- Ein Kern ist die Kombination aus Threads und den geteilten Ressourcen
- Kerne teilen sich wiederum die Cachehierarchie und arbeiten groesstenteils unabhaengig
- Multithreading Architekturen unterscheiden sich darin, wie sich Threads, Ressourcen teilen
## Architekturen
- Einfaches Multithreading
	- Threads wechseln sich zu einem festen Takt ab
 - Simultaneous Multithreading
	 - Threads laufen echt parallel, falls sie unterschiedliche Teile der Ressourcen benoetigen
#### Beispiel
![[Pasted image 20230125155911.png]]
## Cacheorganisation
- Manche [[Cache|Caches]] werden von mehreren Kernen geteilt
- Bei Schreibzugriffen geht die Kohaerenz der Daten verloren
- Die Cachekohaerenz kann mithilfe von Protokollen gewahrt werden
#### MESI Protokoll
- Bei dem MESI Protokoll wird die Kohaerenz von Caches mithilfe eines Automaten gewahrt
###### Zustaende
- Modified
	- Eine Cachezeile wurde lokal veraendert
- Exclusive
	- Wert liegt in genau einer Cachezeile vor
- Shared
	- Wert liegt in mindestens zwei Cachezeilen vor
- Invalid
	- Wert ist nicht gueltig
###### Beispiel
![[Pasted image 20230130122858.png]]
#### False Sharing
- Schreiben mehrere Threads auf nicht ausgerichtete Daten, so kommt es zu zusaetzlichen Misses im Cache, da die Daten staendig ueberschrieben und neu geladen werden
- False Sharing kann durch die Ausrichtung von Daten vermieden werden
###### Beispiel
![[Pasted image 20230130125256.png]]