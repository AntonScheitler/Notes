## Anforderungen
- Eine Datenstruktur fuer eine Sequenz muss Operationen zum Einfuegen, Lesen, Aendern und Loeschen fuer all ihre Elemente bieten
- Verschiedene Implementierungen bieten unterschiedliche Vor- und Nachteile
## Arrays
- Ein Array ist ein festgelegtes, kontinuierliches Stueck Speicher, auf welches beliebig zugegriffen werden kann
#### Vorteile
- Alle Operationen koennen sehr effizient ausgefuehrt werden, da auf alle Elemente gleich schnell zugegriffen werden kann
#### Nachteile
- Die Groesse eines Arrays muss bei der Initialisierung festgelegt werden
#### Dynamisches Array
- Ist das urspruengliche Array gefuellt, so wird ein neues Array mit groesserer Laenge angelegt
- Die Elemente des urspruenglichen Arrays muessen in das Neue kopiert werden, was in $O(n^2)$ erfolgt
- Im worst-case laeuft das Einfuegen neuer Elemente somit in $O(n^2)$, obwohl es selten zur Anlegung eines neuen Arrays kommt
###### Amortisierte Kosten
- Die effizienten Einfuege-Operationen werden mit der teueren Realloc-Operation verrechnet
- Die durchschnittliche Laufzeit betraegt somit $O(1)$
#### Beispiel
- TODO
## Doppelt verkettete Liste
- Die Daten werden in Elementen abgespeichert, welche jeweils ihren Vorgaenger und Nachfolger referenzieren
#### Splicing
- Eine doppelt verkettete Liste bietet die splice Methode, welche eine Sequenz von Elementen $a, ..., b$ ausschneidet und hinter einem Element $t$ einfuegt
###### Beispiel
![[Pasted image 20230510133347.png]]
#### Beispiel
![[Pasted image 20230510132900.png]]