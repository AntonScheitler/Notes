## Berechenbarkeit
- Eine Funktion $f: \mathbb{N}^k \to \mathbb{N}$ ist intuitiv berechenbar, wenn es einen Algorithmus gibt, der folgende Eigenschaften besitzt:
	- Der Algorithmus terminiert nach endlich vielen Schritten mit dem Ergebnis $f(n_1, ..., n_k)$, falls $f(n_1, ..., n_k)$ definiert ist
	- Der Algorithmus terminiert nicht, falls $f(n_1, ..., n_k)$ nicht definiert ist
- Es gibt nicht berechenbare Funktionen, da die Menge der Algorithmen $\subseteq \Sigma^*$ abzaehlbar und die Menge der Funktionen $\mathbb{N} \to \{0, 1\}$ ueberabzaehlbar ist
#### Funktionsterminologie
- Eine Funktion $f$ ist total, falls sie fuer alle Eingaben definiert ist, partiell, falls sie fuer manche Eingaben undefiniert sein kann und echt partiell, falls sie fuer mindestens eine Eingabe undefiniert ist
## Turing Maschinen
- Eine Funktion ist genau dann berechenbar, wenn sie mit einer Turing Maschine berechnet werden kann
#### Aufbau
- Eine Turing Maschine besteht aus Zustaenden, einem Band, sowie einem Lese- und Schreibkopf
- Das Band enthaelt zu Beginn das Eingabewort, kann jedoch vom Lese- und Schreibkopf beliebig veraendert werden
- Das Verhalten des Kopfes wird von einer Zustandsuebergangsfunktion festgelegt
###### Zustandsuebergangsfunktion
- Die Uebergangsfunktion akzeptiert einen Zustand $q$ und ein Bandzeichen $\gamma$ und liefert einen neuen Zustand $q'$, ein neues Bandzeichen $\gamma '$, sowie die Bewegungsrichtung des Kopfs
- Nach jedem Zustandsuebergang kann sich der Kopf hierbei entweder ein Feld nach links, eines nach rechts, oder garnicht bewegen 
###### Konfiguration
- Die Konfiguration einer Turing Maschine kann ueber $(a, q, b)$ beschrieben werden
- $a$ beschreibt hierbei den Inhalt des Bands, $q$ den Zustand der Maschine und $b$ das Wort auf dem Band, welches rechts vom Kopf liegt
###### k-Band Turing Maschinen
- Eine Turing Maschine kann aus mehreren Baendern bestehen, auf denen mit unabhaengigen Kopefen gleichzeitig gearbeitet wird
- Jede k-Band Turing Maschine kann jedoch auch durch eine Turing Maschine mit nur einem Band simuliert werden
#### Turing-Berechenbarkeit
- Eine Funktion ist Turing-berechenbar, falls es eine Turing Maschine gibt, sodass eine beliebige Eingabe der Funktion folgendes Ergebnis hat:
	- Die Turing Maschine befindet sich in einem Endzustand 
	- Das Band ist leer, bis auf das Ergebnis, welches rechts vom Kopf liegt
###### Akzeptanz von Sprachen
- Mit einer Turing Maschine koennen auch Sprachen erkannt werden
- Insbesondere koennen Typ-0 Sprachen von Turing Maschinen erkannt werden
- Deterministische und nicht deterministische Automaten akzeptieren zudem dieselbe Sprache
###### Halten
- Erreicht eine Turing Maschine einen Endzustand, so haelt sie sofort
#### Aequivalenz zu Programmiersprachen
- Durch das Hintereinanderschalten von Turing Maschinen, koennen if und while statements simuliert werden
- Das bedeutet, dass Turing Maschinen genauso maechtig sind, wie while oder goto Programme
## Entscheidbarkeit
- Eine Menge $A$ ist entscheidbar, falls ihre charakteristische Funktion berechenbar ist:
$$\chi_A(x) = \begin{cases}
1, \; x \in A \\
0, \; x \notin A
\end{cases}$$
- Eine Eigenschaft $P(x)$ ist zudem entscheidbar, falls $\{x \mid P(x)\}$ entscheidbar ist
#### Halteproblem
- Durch Widerspruch kann bewiesen werden, dass nicht entschieden werden kann, ob ein Programm terminiert oder nicht
- Koennte dies entschieden werden, so koennte man eine Funktion $f$ definieren, sodass:
$$f(x) = \begin{cases}
0, \; x(x) \text{ terminiert nicht} \\
\perp, \; x(x) \text{ terminiert}
\end{cases}$$
- $f(f)$ fuehrt somit zu einem Widerspruch
#### Reduktion
- Eine Menge $A \subseteq \Sigma^*$ ist reduzierbar auf $B \subseteq \Gamma^*$, sodass $A \leq B$, falls es eine Funktion $f$ gibt mit:
$$\forall w \in \Sigma^*: w \in A \Leftrightarrow f(w) \in B$$
- Mithilfe der Reduktion koennen somit unbekannte Probeme auf bekannte reduziert und geloest werden
###### Regeln
- Ist $A$ unentscheidbar, so auch $B$
- Ist $B$ entscheidbar, so auch $A$
#### Semientscheidbarkeit
- Eine Menge $A$ ist semi-entscheidbar, falls folgende Funktion berechenbar ist:
$$\chi_A'(x) = \begin{cases}
1, \; \text{falls} \; x \in A \\
\perp, \; \text{falls} \; x \notin A \\
\end{cases}$$
- Falls $A$ somit entscheidbar ist, so ist es auch semi-entscheidbar
- Zudem kann ein Problem auf ein semi-entscheidbares Problem reduziert werden, um zu zeigen, dass es semi-entscheidbar ist
###### Rekursive Aufzaehlbarkeit
- Eine Menge $A$ ist rekursiv aufzaehlbar, falls es eine berechenbare Funktion $f$ gibt, sodass:
$$A = \{f(0), f(1), f(2), ... \}$$
- $A$ ist genau dann rekursiv aufzaehlbar, wenn es semi-entscheidbar ist  
#### Satz von Rice
- Es sei $F$ eine Menge von berechenbaren Funktionen mit $F \neq \emptyset$ und $F \neq \text{alle berechenbaren Funktionen}$
- Es ist unentscheidbar, ob die von einer Turing Maschine $M_w$ berechnete Funktion $\varphi_w$ in $F$ enthalten ist
- Alle nicht-triviale semantische Eigenschaften von Programmen sind somit unentscheidbar