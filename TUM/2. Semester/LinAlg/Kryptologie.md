## Pohlig-Hellman Verfahren
- Es sei $S$ der Sender einer Nachricht $N \in \mathbb{Z}^{\star}_p$ und $R$ ihr Empfaenger, wobei $p$ eine beliebige, aber grosse Primzahl ist
#### Verschluesselung
- Es wird ein $e$ gewaehlt, sodass $ggT(e, p-1) = 1$ ist
- Somit ist $e \in \mathbb{Z}^{\star}_{p-1}$ und besitzt ein Inverses
- $N$ wird ueber $e$ zu $N^e$ verschluesselt
#### Entschluesselung
- Da $e$ ein Inverses besitzt, kann ueber den euklidischen Algorithmus ein $d$ bestimmt werden, sodass gilt:
$$ed = 1 \mod p-1$$
- Mithilfe von $d$ kann $N^e$ entschluesselt werden:
$$(N^e)^d = N^{ed} = N^{1 + r(p-1)} = N * N^{r(p-1)} = N * (N^{p-1})^r = N * 1^r = N$$
## RSA Verfahren
- Es sei $S$ der Sender einer Nachricht $N \in \mathbb{Z}^{\star}_n$ und R ihr Empfaenger
- Zudem stellt $S$ einen public Key $(n, e)$ zur Verfuegung
#### Public Key
- $n$ setzt sich folgendermassen aus dem beiden Primzahlen $p$ und $q$ zusammen:
$$n = pq$$
- Fuer die [[Restklassengruppen|prime Restklassengruppe]] $\mathbb{Z}^{\star}_n$ gilt somit:
$$|\mathbb{Z}^{\star}_n| = \varphi(n) = (p-1)(q-1)$$
- $e$ wird so bestimmt, dass gilt:
$$gTT(e, (p-1)(q-1)) = 1$$
- Somit ist $e \in \mathbb{Z}^{\star}_{(p-1)(q-1)}$ und bestizt ein Inverses
- $N$ wird ueber $e$ zu $N^e$ verschluesselt
#### Private Key
- Da $e$ ein Inverses besitzt, kann ueber den euklidischen Algorithmus ein $d$ bestimmt werden, sodass gilt:
$$ed = 1 \mod (p-1)(q-1)$$
- Dieses $d$ wird geheim gehalten und kann $N^e$ entschluesseln:
$$(N^e)^d = N^{ed} = N^{1 + r(p-1)(q-1)} = N^1 * (N^{(p-1)(q-1)})^r = N * 1^r = N$$