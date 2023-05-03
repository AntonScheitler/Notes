## Gruppen
- Es sei $\mathbb{G}$ eine Menge mit der Verknuepfung $\cdot$
- Man bezeichnet $(\mathbb{G}, \cdot)$ als Gruppe, falls folgende Kriterien erfuellt sind:
	1. Abgeschlossenheit
	$$\forall \space a, b \in \mathbb{G}:a \cdot b \in \mathbb{G}$$
	2. Assoziativitaet
	$$\forall a, b, c \in \mathbb{G}: (a \cdot b) \cdot c = a \cdot (b \cdot c)$$
	 3. Neutrales Element
	$$\exists \space e \in \mathbb{G}: \forall \space a \in \mathbb{G}: a \cdot e = a$$
	 4. Inverses Element
	$$\forall \space a \in \mathbb{G}: \exists \space a^{-1} \in \mathbb{G}: a \cdot a^{-1} = e$$
#### Abelsche Gruppen
- Es sei $(G, \cdot)$ eine beliebige Gruppe
- Man bezeichnet diese Gruppe als abelsch, falls gilt:
$$\forall \space a, b \in \mathbb{G}: a \cdot b = b \cdot a$$
## Untergruppen
- Es sei $(\mathbb{G}, \cdot)$ eine beliebige Gruppe
- Man bezeichnet $(\mathbb{U}, \cdot)$ als eine Untergruppe von $(\mathbb{G}, \cdot)$, falls folgende Kriterien erfuellt sind:
	1. Teilmengenbeziehung
	$$\mathbb{U} \subseteq \mathbb{G}$$
	 2. Abgeschlossenheit
	$$\forall \space a, b \in \mathbb{U}: a \cdot b \in \mathbb{U}$$
	 3. Neutrales Element
	$$\exists \space e \in \mathbb{U}: \forall \space a \in \mathbb{U}: a \cdot e = a$$
	 4. Inverses Element
	$$\forall \space a \in \mathbb{U}: \exists \space a^{-1} \in \mathbb{U}: a \cdot a^{-1} = e$$
#### Erzeugte Untergruppen
- Es sei $(\mathbb{G}, \cdot)$ eine Gruppe und $a \in \mathbb{G}$
- Ausgehend von $a$ wird eine erzeugte Untergruppe definiert durch:
$$\langle a \rangle = \{a^k \space | \space k \in \mathbb{Z}\} \subseteq \mathbb{G}$$
- Das neutrale Element ist hierbei $e = a^0$
###### Ordnung eines Elements
- Es sei $\langle a \rangle$ die durch $a$ erzeugte Untergruppe
- Die Ordunung $ord(a)$ von $a$ wird definiert durch:
$$ord(a) = |\langle a \rangle| = \begin{cases}
n \\
\infty
\end{cases}$$
- Falls $ord(a)$ endlich ist, so ist $ord(a)$ ist zudem die kleinste natuerliche Zahl, fuer die gilt:
$$a^{ord(a)} = e$$
## Ringe
- Es sei $\mathbb{G}$ eine Gruppe mit den beiden Verknuepfungen $+$ und $\cdot$
- Man bezeichnet $(\mathbb{G}, +, \cdot)$ als Ring, falls folgende Kriterien erfuellt sind:
	- $(\mathbb{G}, +)$ bildet eine abelsche Gruppe
	- $\cdot$ ist assoziativ
	 - Es gelten die Distributivgesetze:
	$$\forall \space a, b, c \in \mathbb{G}: a \cdot (b + c) = (a \cdot b) + (a \cdot c)$$
#### Kommutativer Ring
- Ein Ring $(\mathbb{G}, +, \cdot)$ ist kommutativ, falls gilt:
$$\forall \space a, b \in \mathbb{G}: a \cdot b = b \cdot a$$
#### Ring mit Einselement
- Ein Ring $(\mathbb{G}, +, \cdot)$ besitzt ein Einselement, falls gilt:
$$\exists \space e \in \mathbb{G}: \forall \space a \in \mathbb{G}: a \cdot e = a$$
## Koerper
- Es sei $\mathbb{G}$ eine Menge mit den Verknuepfungen $+$ und $\cdot$
- Man bezeichnet $(\mathbb{G}, +, \cdot)$ als Koerper, falls folgende Kriterien erfuellt sind:
	- $(\mathbb{G}, +)$ bildet eine abelsche Gruppe
	- $(\mathbb{G} \setminus \{0\}, \cdot)$ bildet eine abelsche Gruppe
	 - Es gelten die Distributivgesetze:
	$$\forall \space a, b, c \in \mathbb{G}: a \cdot (b + c) = (a \cdot b) + (a \cdot c)$$