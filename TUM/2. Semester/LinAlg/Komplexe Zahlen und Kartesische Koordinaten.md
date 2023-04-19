## Grundlagen von komplexen Zahlen
- Die [[Konstruktion der komplexen Zahlen]] erfolgt mithilfe der Menge $\mathbb{R}^2$
- Es sei $z$ eine beliebige Zahl aus $\mathbb{C} = \{a + bi | a, b \in \mathbb{R}\}$ 
- Man bezeichnet $Re(z) = a$ als Realteil und $Im(z) = b$ als Imaginaerteil von $z$
- Eine beliebige Zahl $w$ ist zu $z$ aequivalent, falls Real- und Imaginaeteil der beiden Zahlen identisch sind
#### Konjugiert komplexe Zahlen
- Man bezeichnet $\overline{z}=a -bi$ als die zu $z$ konjugiert komplexe Zahl
- $\overline{z}$ entsteht somit durch die Spiegelung von $z$ an der reellen Achse
- Fuer $\overline{z}$ gilt:
$$z\overline{z} = (a + bi) \cdot (a - bi) = a^2 + b^2 \in \mathbb{R}$$
$$\overline{z+w} = \overline{z} + \overline{w}$$
$$\overline{z \cdot w} = \overline{z} \cdot \overline{w}$$
#### Betrag einer komplexen Zahl
- Der Abstand $|z|$ einer komplexen Zahl $z$ zum Ursprung bezeichnet man als Betrag von $z$
- Der Abstand von $z$ zu einer komplexen Zahl $w$ wird durch $|z - w|$ beschrieben 
- Fuer $|z|$ gilt:
$$|z| = \sqrt{a^2 + b^2} = \sqrt{z\overline{z}}$$
#### Multiplikative Inverse einer komplexen Zahl
- Sei $q = \frac{z}{w}$ eine komplexe Zahl
- Fuer das multiplikative Inverse von $q$ gilt:
$$q^{-1}=q^{-1} \cdot \frac{\overline{w}}{\overline{w}}$$
#### Dreiecksungleichung
- Fuer zwei komplexe Zahlen $z$ und $w$ gilt:
$$|zw| = |z| \cdot |w|$$
$$|z + w| \leq |z| + |w|$$
## Fundamentalsatz der Algebra
- Jedes Polynom $f = a_nx^n + ... + a_1x + a_0$ mit komplexen Koeffizienten $a_n ... a_0$ kann folgendermassen in Linearfaktoren zerlegt werden:
$$f = a_n(x - z_n)^{v_n} + ... + (x - z_1)^{v_1}$$
 - Hierbei sind $z_n ... z_1$ Nullstellen von $p$ mit den Vielfachheiten $v_n ... v_1$
 - Die Zerlegung kann durch wiederholtes Bestimmen der Nullstellen und Polynomdivision ermittelt werden