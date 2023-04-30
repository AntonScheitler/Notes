## Eliminationsverfahren
- Ein [[Lineare Gleichungssysteme|LGS]] kann geloest werden, indem es in seine Zeilenstufenform ueberfuehrt wird
- Die Umformung erfolgt mithilfe elementarer Zeilenumformungen
- Nach Erreichen der Zeilenstufenform koennen die Loesungen des LGS durch Rueckwaertseinsetzen bestimmt werden
#### Zeilenumformungen
- Vertauschen zweier Zeilen
- Multiplikation einer Zeile mit einem $\lambda \neq 0$ 
- Addition des $\lambda$-fachen einer Zeile zu einer anderen Zeile
#### Beispiel
$$\begin{pmatrix}
1 & 1 & 2 &| & 2 \\
2 & 2 & -1 &| & 1 \\
3 & 4 & 2 & | & 2
\end{pmatrix}
\leadsto 
\begin{pmatrix}
1 & 1 & 2 & | & 2 \\
0 & 1 & -4 & | & -4 \\
0 & 0 & -5 & | & -3
\end{pmatrix}
$$ 
## Rang einer Matrix
- Mithilfe elementarer Zeilenumformungen kann jede beliebige [[Matrizen|Matrix]] $A$ auf Zeilenstufenform gebracht werden
- Die Anzahl der Zeilen, die ungleich 0 sind, bezeichnet man als den Rang $rg(A)$ dieser Matrix
#### Bedeutung fuer LGS
- Es sei $n$ die Anzahl der Variablen in einem LGS und $A$ seine zugehoerige Koeffizientenmatrix
- Fuer ein LGS gilt:
	- Es gibt keine Loesungen, falls $rg(A) \neq rg(A|b)$ ist
	- Es gibt genau eine Loesung, falls $n = rg(A)$ ist
	- Es gibt unendlich viele Loesungen, falls $n > rg(A)$
## Homogene LGS
- Ein LGS mit $(A|0)$ bezeichnet man als homogenes LGS
- Jedes LGS mit $(A|b)$ besitzt ein zugehoeriges homogenes LGS mit $(A|0)$ 
#### Loesungen eines homogenen LGS
- Jedes homogene LGS besitzt die triviale Loesung $(0, ..., 0)$
- Sind $(k_1,  ..., k_n)$ und $(l_1, ..., l_n)$ Loesungen eines homogenen LGS, so sind auch $(k_1, ..., k_n) + (l_1, ..., l_n)$, sowie $\lambda \cdot (l_1, ..., l_n)$ Loesungen dieses LGS
- Ist $(A|b)$ ein loesbares LGS mit der Loesungsmenge $L$ und besitzt (A|0) die Loesungsmenge $L_h$, so gilt fuer eine beliebige Loesung $x$ von $(A|b)$:
$$L = \{x + y \space | \space y \in L_h \}$$