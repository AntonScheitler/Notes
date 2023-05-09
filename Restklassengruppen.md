## Restklassen
- Es sei $n \in \mathbb{N}$ und $a \in \mathbb{Z}$ 
- Fuer jedes $a$ wird die Menge $\overline{a}$ konstruiert durch:
$$\overline{a} = \{a + nz \space | \space z \in \mathbb{Z}\}$$
- Es sei nun auch $m \in \mathbb{Z}$ beliebig mit $q \in \mathbb{Z}$ und $r \in \{0, ..., n-1\}$
- Ein solches $m$ kann stets durch die Division von $n$ mit Rest dargestellt werden:
$$m = qn + r$$
- Fuer dieses $m$ gilt somit:
$$m \in r + n\mathbb{Z} = \overline{r}$$
- Hieraus folgt, dass die Mengen $\overline{r}$, $\mathbb{Z}$ partitionieren
- Die Mengen $\overline{r}$ bezeichnet man als Restklassen modulo $n$
#### Kongruenz
- Fuer beliebige $a, b \in \mathbb{Z}$ wird die Kongruenz modulo $n$ beschrieben durch:
$$a \equiv b \space \mod{n}$$
- $a$ und $b$ haben somit bei der Division durch $n$ mit Rest denselben Rest
## Restklassengruppen
- Es sei ${\mathbb{Z}_n} = \{\overline{0}, ..., \overline{n - 1}\}$ fuer ein beliebiges $n \in \mathbb{N}$
- Auf der Menge ${\mathbb{Z}_n}$ werden Operationen definiert
#### Addition
- Es seien $\overline{k}, \overline{l} \in \mathbb{Z}_n$
- Die Addition dieser Elemente wird definiert durch:
$$\overline{k} + \overline{l} = \overline{k + l}$$
- Die [[Algebraische Strukturen|Gruppe]] $(\mathbb{Z}_n, +)$ ist somit abelsch
#### Multiplikation
- Es seien $\overline{k}, \overline{l} \in \mathbb{Z}_n$
- Die Mulitplikation dieser Elemente wird definiert durch:
$$\overline{k} \cdot \overline{l} = \overline{k \cdot l}$$
- Diese Operation besitzt ein Nullelement und ist kommutativ
- $(\mathbb{Z}_n, +, \cdot)$ ist somit ein kommutativer Ring mit Einselement