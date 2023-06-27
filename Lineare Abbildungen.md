## Allgemeines
- Es seien $K, W$ beliebige $\mathbb{K}$-[[Vektorraeume]]
- Zwischen $K$ und $W$ wird die Abbildung $f$ definiert ueber:
$$\forall \space v \in V: \exists_1 \space w \in W: f(v) = w$$
- $f$ ist linear, beziehungsweise ein Homomorphismus, falls fuer beliebige $v, u \in V$ und $\lambda \in \mathbb{K}$ gilt:
$$f(\lambda v) = \lambda f(v)$$
$$f(v + u) = f(v) + f(u)$$
$$f(0) = 0$$
- Die Komposition beliebiger linearer Funktionen ist ebenfalls linear
- Ist $f$ linear und bijektiv, so bezeichnet man es als Isomorphismus
#### Darstellungsmatrizen
- Es sei $f: \mathbb{K}^n \mapsto \mathbb{K}^m$ eine lineare Abbildung definiert ueber:
$$TODO$$
###### Kernformel
- Fuer den [[Lineare Gleichungssysteme|Kern]] von $f: V \mapsto W$ gilt:
$$Ker(f) = \{ v \in V \mid f(v) = 0 \} \leq V$$
###### Bildformel
- Fuer das Bild von $f: V \mapsto W$ gilt:
$$Bild(f) = \{f(v) \mid v \in V \} \leq W$$
###### Dimensionsformel
- Fuer eine lineare Abbildung $f: V \mapsto W$ gilt:
$$dim(Ker(f)) = def(f)$$
$$dim(Bild(f)) = rg(f)$$
$$dim(V) = def(f) + rg(f)$$
- $f$ ist genau dann injektiv, wenn $Ker(f) = \{ 0 \}$
- TODO