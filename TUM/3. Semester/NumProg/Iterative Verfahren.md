## Fixpunkte
- Ein Punkt $x_i$ ist ein Fixpunkt einer Funktion $f$, falls gilt:
$$f(x_i) = x_i$$
- Bei einem Fixpunkverfahren wird eine Funktion $\phi$ konstruiert, die wiederholt auf einen Startpunkt $x_i$ angewandt wird
- Veraendert sich die Ausgabe von $\phi$ nach einem Schritt nicht, so wurde die Loesung erreicht
- Die Loesung ist somit ein Fixpunkt von $\phi$
## Relaxationsmethoden
- Um die Loesungen [[Lineare Gleichungssysteme|linearer Gleichungssysteme]] mit sproadischen Matrizen zu approximieren, werden iterative Fixpunktverfahren verwendet
- $x^{(i)}$ ist hierbei die approximierte Loesung im $i$-ten Schritt, wobei $x^{(0)}$ beliebig gewaehlt wird
#### Residuum
- Das Residuum einer Loesung $x^{(i)}$ wird definiert durch
$$r^{(i)} = b - Ax^{(i)} = Ax - Ax^{(i)} = -Ae^{(i)}$$
- Das Residuum kann somit genutzt werden um $x^{(i)}$ zu vergenauern
- Hierfuer wird die folgende Funktion konstruiert:
$$x^{(i+1)} = x^{(i)} + M^{-1} (b - Ax^{(i)})$$
- $M$ muss hierbei effizient invertierbar sein und $A$ gut approximieren 
#### Richardson Iteration
- Fuer $M$ wird $E_n$ gewaehlt
- Somit ist $M$ zwar schnell invertierbar, jedoch keine gute Approximation fuer $A$
- Hierbei gilt:
$$x^{(i+1)} = x^{(i)} + E_n^{-1} (b - Ax^{(i)})$$
#### Jacobi Iteration
- Fuer $M$ wird $diag(A)$
- $M$ ist somit relativ schnell invertierbar und approximiert $A$ in etwa 
- Hierbei gilt:
$$x^{(i+1)} = x^{(i)} + diag(A)^{-1} (b - Ax^{(i)})$$
#### Gauss-Seidel Iteration
- Das Residuum wird komponentenweise bestimmt, wobei das Residuum durch das Verwenden neuer Approximationen genauer wird:
$$r_k^{(i)} = b_k - \sum_{j = 1}^{k - 1} a_{kj}x_j^{(i + 1)} - \sum_{j = k}^{n}a_{kj}x_j^{(i)}$$
- Die Approximation $x^{(i)}$ wird ebenso komponentenweise bestimmt:
$$x_k^{(i+1)} = x_k^{(i)} + \frac{1}{a_{kk}} \cdot r_k^{(i)}$$
#### Methode des steilsten Abstiegs
- Fuer $M$ wird keine Matrix gewaehlt
- Stattdessen wird das Residuum mit einer optimalen Schrittweite $\alpha^{(i)}$ gestreckt:
$$\alpha^{(i)} = \frac{r^{(i)^T}r^{(i)}}{r^{(i)^T}Ar^{(i)}}$$
- Hierbei gilt:
$$x^{(i + 1)} = x^{(i)} + \alpha^{(i)}r^{(i)}$$
## Nullstellenapproximation
- Um Nullstellen iterativ zu approximieren, koennen unterschiedliche Verfahren verwendet werden
#### Newton Verfahren
- Die Tangente einer Funktion $f$ zu einem Startpunkt $x^{(0)}$ wird berechnet und ihre Nullstelle ermittelt
- Diese Nullstelle dient als Startpunkt fuer den naechsten Iterationsschritt
- Somit gilt:
$$x^{(k + 1)} = x^{(k)} - \frac{f(x^{(k)})}{f'(x^{(k)})}$$
###### Beispiel
![[Pasted image 20240207084111.png]]
#### Sekantenverfahren
- Das Sektantenverfahren erfolgt aehnlich zum Newton Verfahren
- Hierbei wird jedoch nicht die Ableitung gebildet, sondern stattdessen eine Sektante durch zwei Startpunkte konstruiert
###### Beispiel
![[Pasted image 20240207084245.png]]