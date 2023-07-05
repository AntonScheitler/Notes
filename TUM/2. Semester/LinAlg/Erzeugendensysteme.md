## Linearkombinationen
- Es sei $V$ ein $\mathbb{K}$-Vektorraum mit $v_1, ..., v_n \in V$ und $\lambda_1, ..., \lambda_n \in \mathbb{K}$
- Man bezeichnet einen Vektor $v \in V$ als Linearkombination von $v_1, ..., v_n$, falls er dargestellt werden kann durch:
$$v = \lambda_1 v_1 + ... + \lambda_n v_n$$
- Um zu bestimmen ob ein gegebener Vektor $v$ als Linearkombination von $v_1, ..., v_n$ dargestellt werden kann, kann ein [[Lineare Gleichungssysteme|homogenes lineares Gleichungssystem]] verwendet werden
#### Das Erzeugnis
- Fuer $X \subseteq V$ wird definiert:
$$\langle X \rangle = lin(X) = span(X) = \Big \{ \sum_{i = 1}^{n} \lambda_i v_i \mid n \in \mathbb{N}, \lambda_1, ..., \lambda_n \in \mathbb{K}, v_1, ..., v_n \in \mathbb{X} \Big \}$$
- Gilt $\langle X \rangle = U$, so bezeichnet man $X$ als Erzeugendensystem von $U$
#### Lineare Unabhaengigkeit
- Die Vektoren $v_1, ..., v_n$ sind linear unabhaengig, falls gilt:
$$\forall \space T \subset \{v_1, ..., v_n\}: \langle T \rangle \subset \langle v_1, ..., v_n \rangle$$
- Umgekehrt sind die Vektoren linear abhaengig, falls gilt:
$$\exists \space T \subset \{v_1, ..., v_n\}: \langle T \rangle = \langle v_1, ..., v_n \rangle$$
- Sind alle Teilmengen von $\{v_1, ..., v_n\}$ linear unabhaengig, so ist $\{v_1, ..., v_n\}$ linear unabhaengig
###### Kriterium
- Das lineare Gleichungssystem $\lambda_1 v_1 + ... + \lambda_n v_n = 0$ wird aufgestellt
- Hat das LGS genau eine Loesung, so sind die Vektoren linear unabhaengig
- Hat es mehr als eine Loesung, so sind die Vektoren linear abhaengig