## Hash-Tables
- Es sei ein Array der Groesse $m$ und eine Menge $U$ an Schluesseln gegeben
- Dieses Array bietet die Grundlage fuer den Hash-Table
- Elemente werden mithilfe einer Hashfunktion ueber ihren Schluessel in das Array eingefuegt
#### Hashfunktion
- Die Hashfunktion $h$ bildet Schluessel auf Indizes im Array ab:
$$h: U \mapsto \{0, ..., m-1\}$$
- Eine Hashfunktion ist zeiteffizient, und verfuegt ueber eine grosse Streuung
## Kollisionen
- Werden Elemente mit unterschiedlichen Schluesseln den selben Index abgebildet, so kommt es zu einer Kollision
- Kollisionen koennen auf unterschiedliche Weisen behandelt werden
#### Hashing with Chaining
- Das Array des Hash-Tables besteht aus Listen
- Werden Elemente mehrmals auf einen Index abgebildet, werden sie in die entsprechende Liste eingefuegt
###### Beispiel
![[Pasted image 20230524130208.png]]
#### Hashing mit linearem Sondieren
- Elemente werden mit ihrem gegebenen Index $I$ im Array eingefuegt
- Ist der Index $I$ bereits von einem anderen Element belegt, so wird versucht, das Element an den darauffolgenden Indizes einzufuegen
- Das Suchen von Elementen muss entsprechend angepasst werden
###### Beispiel
![[Pasted image 20230524153935.png]]
#### Double Hashing
- Aehnlich wie beim linearen Sondieren, wird durch das Array iteriert, um einen passenden Index fuer ein gegebenes Element zu bestimmen
- Die Schrittweite bei der Iteration wird durch eine zweite Hashfunktion angegeben:
$$h(k, i) = h(k) + i * h'(k) \mod m$$