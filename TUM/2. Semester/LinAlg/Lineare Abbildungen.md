## Allgemeines
- Es seien $K, W$ beliebige $\mathbb{K}$-[[Vektorraeume]]
- Zwischen $K$ und $W$ wird die Abbildung $f$ definiert ueber:
$$\forall \space v \in V: \exists_1 \space w \in W: f(v) = w$$
- $f$ ist linear, beziehungsweise ein Homomorphismus, falls fuer beliebige $v, u \in V$ und $\lambda \in \mathbb{K}$ gilt:
$$f(\lambda v) = \lambda f(v)$$
$$f(v + u) = f(v) + f(u)$$
$$f(0) = 0$$
- Die Komposition beliebiger linearer Funktionen ist ebenfalls linear
#### Kernformel
- Fuer den [[Lineare Gleichungssysteme|Kern]] von $f: V \mapsto W$ gilt:
$$Ker(f) = \{ v \in V \mid f(v) = 0 \} \leq V$$
#### Bildformel
- Fuer das Bild von $f: V \mapsto W$ gilt:
$$Bild(f) = \{f(v) \mid v \in V \} \leq W$$
#### Dimensionsformel
- Fuer eine lineare Abbildung $f: V \mapsto W$ gilt:
$$def(f) = dim(Ker(f))$$
$$rg(f) = dim(Bild(f))$$
$$dim(V) = def(f) + rg(f)$$
- $f$ ist genau dann injektiv, wenn $Ker(f) = \{ 0 \}$
- Ist $f$ injektiv und $dim(V) = dim(W)$, so ist $f$ auch surjektiv und somit bijektiv
- Ist $f$ bijektiv, so bezeichnet man $f$ als Isomorphismus
## Koordinatenvektoren
- Es sei $B = (b_1, ..., b_n)$ eine geordnete [[Basen von Vektorraeumen|Basis]] von $V$
- Fuer die Elemente von V gilt somit:
$$\forall \space v \in V: \exists_1 \space Lk = \lambda_1 b_1 + ... + \lambda_n b_n$$
- Auf $V$ bezueglich $B$ wird folgende Abbildung definiert:
$${_B\underline{\cdot}} = \begin{cases}
V \rightarrow \mathbb{K}^n \\
v \mapsto (\lambda_1, ..., \lambda_n)^T
\end{cases}$$
- Der Koordinatenvektor von $v$ wird beschrieben durch:
$${_Bv} = (\lambda_1, ..., \lambda_n)$$
- $B$ ist ein Isomorphismus
## Darstellungsmatrizen
- Es seien $V$ und $W$ Vektorraeume mit den Basen $B = (b_1, ..., b_n)$ und $C = (c_1, ..., c_m)$
- Es sei $f: V \mapsto W$ eine beliebige Abblidung
- Die Darstellungsmatrix $M$ von $f$ bezueglich der Basen $B$ und $C$ wird definiert durch:
$$_CM(f)_B = (_Cf(b_1), ..., {_Cf}(b_n)) \in \mathbb{K}^{m \times n}$$
- In der $i$-ten Spalte steht somit der Koordinatenvektor des Bildes des $i$-ten Basisvektors
#### Abbildung ueber Darstellungsmatrizen
- Es sei $v \in V$ beliebig
- Hierbei gilt:
$$_Cf(v) = {_CM}(f)_B \cdot _Bv$$
#### Basistransformationsformel
- Es seien $V, W$ und $U$ Vektorraeume mit dem Basen $B, C$ und $D$ und die Abbildungen $f: V \mapsto W$ und $g: W \mapsto U$ linear
- Hierbei gilt:
$$_DM(g \circ f)_B = {_DM}(g)_C \cdot {_CM}(f)_B$$
- Mithilfe der Darstellungsmatrix $A = {_{E_n}M}(f)_{E_n}$ kann die Darstellungsmatrix von $f$ bezueglich der Basis $B = (b_1, ..., b_n)$ gebildet werden ueber:
$$_BM(f)_B = B^{-1} A B$$