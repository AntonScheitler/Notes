## Anforderungen
- Eine Datenstruktur fuer eine Sequenz muss Operationen zum Einfuegen, Lesen, Aendern und Loeschen fuer all ihre Elemente bieten
- Verschiedene Implementierungen bieten unterschiedliche Vor- und Nachteile
## Arrays
- Ein Array ist ein festgelegtes, kontinuierliches Stueck Speicher, auf welches beliebig zugegriffen werden kann
#### Vorteile
- Alle Operationen werden sehr effizient ausgefuehrt, da auf alle Elemente gleich schnell zugegriffen werden kann
#### Nachteile
- Die Groesse eines Arrays muss bei der Initialisierung festgelegt werden
#### Dynamisches Array
- Ist das urspruengliche Array voll, so wird ein neues Array mit groesserer Laenge angelegt
- Die Elemente des urspruenglichen Arrays muessen in das Neue kopiert werden, was in $O(n)$ erfolgt
- Im worst-case laeuft das Einfuegen neuer Elemente somit in $O(n)$, obwohl es selten zur Anlegung eines neuen Arrays kommt
###### Amortisierte Kosten
- Die effizienten Einfuege-Operationen werden mit der teueren Kopier-Operation verrechnet
- Die durchschnittliche Laufzeit betraegt somit $O(1)$
#### Beispiel
![[Pasted image 20230513192742.png]]
## Doppelt verkettete Liste
- Die Daten werden in Elementen abgespeichert, welche jeweils ihren Vorgaenger und Nachfolger referenzieren
#### Vorteile
- Da sich eine Liste dynamisch veraendern laesst, werden keine teueren Kopier-Operationen benoetigt
- Bestimmte Operationen, wie das Splicing, sind nur auf Listen moeglich
#### Nachteile
- Such-Operationen laufen in $O(n)$
#### Splicing
- Eine doppelt verkettete Liste bietet die splice Methode, welche eine Sequenz von Elementen $a, ..., b$ ausschneidet und hinter einem Element $t$ einfuegt
###### Beispiel
![[Pasted image 20230510133347.png]]
#### Beispiel
![[Pasted image 20230510132900.png]]