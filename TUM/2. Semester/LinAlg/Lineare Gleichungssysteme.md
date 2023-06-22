## Allgemeines
- Ein Lineares Gleichungssystem (LGS) besteht aus $m$ Gleichungen mit $n$ Variablen:
$$a_{11}x_1 + ... +  a_{1n}x_n = b_1$$
$$\vdots$$
$$a_{m1}x_1 + ... + a_{mn}x_n = b_m$$
- Eine Loesung eines LGS beschreibt man mithilfe eines Tupels $l = (l_1, ..., l_n)$, welches saemtliche Gleichungen des LGS befriedigt
- Mithilfe des [[Gaussches Eliminationsverfahren|Gausschen Eliminationsverfahrens]] koennen die Loesungen eines LGS bestimmt werden
## Rang einer Matrix
- Mithilfe elementarer Zeilenumformungen kann jede beliebige [[Matrizen|Matrix]] $A$ auf Zeilenstufenform gebracht werden
- Die Anzahl der Zeilen, die nach Umformung ungleich 0 sind, bezeichnet man als den Zeilenrang $rg(A)$ dieser Matrix
- Aehnlich wird der Spaltenrang der Matrix definiert, wobei der Zeilenrang stets dem Spaltenrang entspricht
#### Bedeutung fuer LGS
- Es sei $n$ die Anzahl der Variablen in einem LGS und $A$ seine zugehoerige Koeffizientenmatrix
- Fuer ein LGS gilt:
	- Es gibt keine Loesungen, falls $rg(A) \neq rg(A|b)$ ist
	- Es gibt genau eine Loesung, falls $n = rg(A)$ ist
	- Es gibt unendlich viele Loesungen, falls $n > rg(A)$
###### Kern einer Matrix
- Der Kern einer Matrix $A$ ist wird definiert durch:
$$Ker(A) = \{x \mid Ax = 0\}$$
- Fuer die Dimension eines Kerns gilt:
$$dim(Ker(A)) = n - rg(A)$$
- Der Kern kann somit ermittelt werden, indem ein [[Erzeugendensysteme|Erzeugendensystem]] der Loesungen von $Ax = 0$ bestimmt wird
- A ist invertierbar, falls $Ker(A) = 0$ ist
## Homogene LGS
- Ein LGS mit $(A|0)$ bezeichnet man als homogenes LGS
- Jedes LGS mit $(A|b)$ besitzt ein zugehoeriges homogenes LGS mit $(A|0)$ 
#### Loesungen eines homogenen LGS
- Jedes homogene LGS besitzt die triviale Loesung $(0, ..., 0)$
- Sind $(k_1,  ..., k_n)$ und $(l_1, ..., l_n)$ Loesungen eines homogenen LGS, so sind auch $(k_1, ..., k_n) + (l_1, ..., l_n)$, sowie $\lambda \cdot (l_1, ..., l_n)$ Loesungen dieses LGS
- Ist $(A|b)$ ein loesbares LGS mit der Loesungsmenge $L$ und besitzt (A|0) die Loesungsmenge $L_h$, so gilt fuer eine beliebige Loesung $x$ von $(A|b)$:
$$L = \{x + y \space | \space y \in L_h \}$$