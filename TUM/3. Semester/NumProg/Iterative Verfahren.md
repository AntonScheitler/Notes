## Relaxationsmethoden
- Um die Loesungen [[Lineare Gleichungssysteme|linearer Gleichungssysteme]] mit sproadischen Matrizen zu approximieren, werden iterative Verfahren verwendet
- $x^{(i)}$ ist hierbei die approximierte Loesung im $i$-ten Schritt, wobei $x^{(0)}$ beliebig gewaehlt wird
#### Residuum
- Das Residuum einer Loesung $x^{(i)}$ wird definiert durch
$$r^{(i)} = b - Ax^{(i)} = Ax - Ax^{(i)} = -Ae^{(i)}$$
- Das Residuum kann somit genutzt werden um $x^{(i)}$ zu vergenauern
#### Richardson Iteration
- Das Residuum wird direkt genutzt, um den naechsten Approximanten zu bestimmen:
$$x^{(i + 1)} = x^{(i)} + r^{(i)}$$
#### Jacobi Iteration
- Fuer jedes $k \in \{1, ..., n\}$ wird ein Aktualisierungswert $y_k$ bestimmt:
$$y_k = \frac{1}{a_{kk}} \cdot r_k^{(i)}$$
- Der naechste Approximant wird dann bestimmt ueber:
$$x^{(i + 1)} = x^{(i)} + y$$
#### Gauss-Seidel Iteration
- Aehnlich zur Jacobi Iteration wird fuer jedes $k \in \{1, ..., n\}$ ein $y_k$ bestimmt, wobei das Residuum auf unterschiedliche Art ermittelt wird:
$$r_k^{(i)} = b_k - \sum_{j = 1}^{k - 1} a_{kj}x_j^{(i + 1)} - \sum_{j = k}^{n}a_{kj}x_j^{(i)}$$
$$y_k = \frac{1}{a_{kk}} \cdot r_k^{(i)}$$
$$x^{(i + 1)} = x^{(i)} + y$$
#### Damping und Over-Relaxation
- Ein Aktualisierungsvektor $y$ wird haeufig mit einer Konstante $0 < \alpha < 1$, beziehungsweise $1 < \alpha < 2$ multipliziert, sodass fuer den naechsten Approximanten gilt:
$$x^{(i + 1)} = x^{(i)} + \alpha y$$
## Minimierungsmethoden
 - 