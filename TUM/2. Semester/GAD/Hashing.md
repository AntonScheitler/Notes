## Hash-Tables
- Es sei ein Array der Groesse $m$ und eine Menge $U$ an Schluesseln gegeben
- Dieses Array bietet die Grundlage fuer den Hash-Table
- Elemente werden mithilfe einer Hashfunktion ueber ihren Schluessel in das Array eingefuegt
#### Hashfunktion
- Die Hashfunktion $h$ bildet Schluessel auf Indizes im Array ab:
$$h: U \mapsto \{0, ..., m-1\}$$
- Eine Hashfunktion ist zeiteffizient, und verfuegt ueber eine grosse Streuung
###### C-Universelle Hashfunktionen
- Eine Menge $H$ von Hashfunktionen $h: U \mapsto \{0, ..., m_1\}$ heisst c-universell, falls fuer jedes Paar $x, y \in U$ gilt:
$$|\{h \in H: h(x) = h(y)\}| \leq \frac{c}{m}|H|$$
#### Beispiel
![[Pasted image 20230702200719.png]]
## Kollisionen
- Werden Elemente mit unterschiedlichen Schluesseln auf den selben Index abgebildet, so kommt es zu einer Kollision
- Kollisionen koennen auf unterschiedliche Weisen behandelt werden
#### Hashing mit Verkettung
- Das Array des Hash-Tables besteht aus Listen
- Werden Elemente mehrmals auf einen Index abgebildet, werden sie in die entsprechende Liste eingefuegt
###### Beispiel
![[Pasted image 20230524130208.png]]
#### Perfektes Hashing
- Elemente werden ueber einen zweistufigen Hashprozess an ihrem Index eingefuegt
- Eine erste Hashfunktion, welche zu wenig Kollisionen fuehrt, bildet jedes Element auf einen Bucket ab
- Da mehrere Elemente auf denselben Bucket abgebildet werden, wird der tatsaechliche Index mithilfe einer zweiten Hashfunktion bestimmt, welche zu keiner Kollision fuehrt
###### Beispiel
![[Pasted image 20230702201430.png]]
#### Hashing mit linearem Sondieren
- Elemente werden mit ihrem gegebenen Index $I$ im Array eingefuegt
- Ist der Index $I$ bereits von einem anderen Element belegt, so wird versucht, das Element an den darauffolgenden Indizes einzufuegen
###### Loeschen von Elementen
- Elemente koennen durch das Einfuegen eines Platzhalters als geloescht markiert werden
- Alternativ koennen alle kollidierenden Elemente des geloeschten Elements verschoben werden, um die enstandene Luecke zu fuellen
###### Beispiel
![[Pasted image 20230524153935.png]]
#### Double Hashing
- Aehnlich wie beim linearen Sondieren, wird durch das Array iteriert, um einen passenden Index fuer ein gegebenes Element zu bestimmen
- Die Schrittweite bei der Iteration wird durch eine zweite Hashfunktion angegeben:
$$h(k, i) = h(k) + i * h'(k) \mod m$$