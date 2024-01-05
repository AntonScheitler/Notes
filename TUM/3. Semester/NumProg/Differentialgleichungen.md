## Allgemeines
- Mithilfe von Differentialgleichungen kann eine Funktion ueber das Verhalten ihrer Ableitungen definiert werden
- Das analytische Loesen einer Differentialgleichung ist in der Regel unmoeglich, weshalb numerische Verfahren zur Approximation genutzt werden muessen
#### Aufbau
- Sei $f$ eine Funktion und $\dot{f}$ ihre Ableitung, so kann eine Differentialgleichung in Abhaengigkeit von der Zeit $t$ aufgestellt werden:
$$\dot{f}(t) = F(t, f(t))$$
## Approximationsverfahren
- Es sei $\dot{f}$ die Ableitung von $f$, wobei die Differentialgleichung $\dot{f}(t) = F(t, f(t))$ gilt
- Die Differentialgleichung wird diskretisiert, indem jedes Vorkommen einer Ableitung durch den Differenzenquotienten ueber ein Zeitintervall $\delta t$ ersetzt wird
- TODO $f(t_k, y_k)$
#### Eulersche Methode
- $y_0$ zum Startzeitpunkt $t_0$ ist gegeben
- Um einen Wert $y_{k + 1}$ zum Zeitpunkt $t_{k + 1} = t_0 + (k + 1) \cdot \delta t$ zu ermitteln, werden der Differenzenquotient $f(t_k, y_k)$, sowie der Wert $y_k$ zum vorherigen Zeitpunkt $t_k$ verwendet
- Hierbei gilt:
$$y_{k + 1} = y_k + \delta t \cdot f(t_k, y_k)$$
###### Beispiel
![[Pasted image 20240105121149.png]]
#### Heunsche Methode
- Mithilfe der eulerschen Methode werden die Werte $y_k$ und $y_{k+1}$ bestimmt
- Der Durchschnitt der Steigungen $f(t_k, y_k)$ und $f(t_{k + 1}, y_{k + 1})$ wird ermittelt, um die tatsaechliche Steigung zum Zeitpunkt $t_k$ besser zu approximieren 
- Die Anzahl der Auswertungen von $f$ verdoppelt sich hierdurch jedoch
#### Runge-Kuttasche Methode
- Zwischen den Zeitpunkten $t_k$ und $t_{k + 1}$ werden zwei zusaetzliche Stuetzpunkte definiert
- Die Steigungen $f(t_k, y_k)$ und $f(t_{k + 1}, y_{k + 1})$, sowie die an den Stuetzpunkten wird fuer eine bessere Approximation der Steigung zum Zeitpunkt $t_k$ genutzt
- Die Anzahl der Auswertungen von $f$ wird somit vervierfacht
#### Mehrschrittmethode
- Um $y_{k+1}$ zu ermitteln, werden die Differenzenquotienten $f(t_k, y_k)$ und $f(t_{k-1}, y_{k-1})$ verwendet
- Mithilfe von Extrapolation kann $y_{k + 1}$ somit besser approximiert werden, ohne, dass $f$ oefter ausgewertet werden muss
- Fuer $y_{k + 1}$ gilt hierbei:
$$y_{k + 1} = y_k + \frac{\delta t}{2} \big (3f(t_k, y_k) - f(t_{k - 1}, y_{k - 1}) \big)$$
- Fuer den ersten Schritt, muss jedoch eine Einschrittmethode verwendet werden
## Fehlerverhalten
- Approximationsverfahren werden anhand ihrer Konsistenz und Konvergenz bewertet
#### Konsistenz
- Der maximale Fehler einer einzelnen Approximation ist der lokale Diskretisierungsfehler
- Ein Verfahren ist konsistent, falls der lokale Diskretisierungsfehler gegen 0 geht, falls $\delta t$ gegen 0 geht
#### Konvergenz
- Der maximale Fehler der Summe aller Approximationen ist der globale Diskretisierungsfehler
- Ein Verfahren ist konvergent, falls der globale Diskretisierungsfehler gegen 0 geht, falls $\delta t$ gegen 0 geht