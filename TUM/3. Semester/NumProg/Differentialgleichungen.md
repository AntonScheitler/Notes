## Allgemeines
- Mithilfe von Differentialgleichungen kann eine Funktion ueber das Verhalten ihrer Ableitungen definiert werden
- Das analytische Loesen einer Differentialgleichung ist in der Regel unmoeglich, weshalb numerische Verfahren zur Approximation genutzt werden muessen
#### Aufbau
- Sei $f$ eine Funktion und $\dot{f}$ ihre Ableitung, so kann eine Differentialgleichung in Abhaengigkeit von der Zeit $t$ aufgestellt werden:
$$\dot{f}(t) = F(t, f(t))$$
## Analytische Verfahren
- In seltenen Faellen ist es moeglich, eine Differentialgleichung analytisch zu loesen:
- Hierfuer wird auf Ableitungen $\dot{y}$ die Leipniz Notation $\frac{dy}{dt}$ angewandt und die Variablen separiert
- Anschliessend wird auf beide Seiten der Gleichung ein Integral angewandt, wobei $y$ durch $\mu$ und $t$ durch $\tau$ ersetzt wird:
$$\int_{y_0}^y ... d\mu = \int_{t_0}^t ... d\tau$$
## Approximationsverfahren
- Es sei $\dot{y}$ die Ableitung von $y$, wobei die Differentialgleichung $\dot{y}(t) = F(t, y(t))$ gilt
- $y$ wird zu jedem Zeitintervall $\delta t$ ausgewertet
- In der Regel bezeichnet $y_k$ den Funktionswert und $f(t_k, y_k)$ die Steigung zum Zeitpunkt $t_k$
#### Explizites Eulerverfahren
- $y_0$ zum Startzeitpunkt $t_0$ ist gegeben
- Um einen Wert $y_{k + 1}$ zum Zeitpunkt $t_{k + 1} = t_0 + (k + 1) \cdot \delta t$ zu ermitteln, werden der Differenzenquotient $f(t_k, y_k)$, sowie der Wert $y_k$ zum vorherigen Zeitpunkt $t_k$ verwendet
- Hierbei gilt:
$$y_{k + 1} = y_k + \delta t \cdot f(t_k, y_k)$$
###### Beispiel
![[Pasted image 20240105121149.png]]
#### Heunsche Methode
- Mithilfe des expliziten Eulerverfahrens werden die Werte $y_k$ und $y_{k+1}$ bestimmt
- Der Durchschnitt der Steigungen $f(t_k, y_k)$ und $f(t_{k + 1}, y_{k + 1})$ wird ermittelt, um die tatsaechliche Steigung zum Zeitpunkt $t_k$ besser zu approximieren 
- Die Anzahl der Auswertungen von $f$ verdoppelt sich hierdurch jedoch
- Somit gilt:
$$y_{k + 1} = y_k + \frac{\delta t}{2} \big (f(t_k, y_k) + f(t_{k+1}, y_k + \delta t \cdot f(t_k, y_k)) \big )$$
#### Runge-Kuttasche Methode
- Zwischen den Zeitpunkten $t_k$ und $t_{k + 1}$ werden zwei zusaetzliche Stuetzpunkte definiert
- Die Steigungen $f(t_k, y_k)$ und $f(t_{k + 1}, y_{k + 1})$, sowie die an den Stuetzpunkten wird fuer eine bessere Approximation der Steigung zum Zeitpunkt $t_k$ genutzt
- Die Anzahl der Auswertungen von $f$ wird somit vervierfacht
#### Mehrschrittmethoden
- Um $y_{k+1}$ zu ermitteln, werden die Differenzenquotienten $f(t_k, y_k)$ und $f(t_{k-1}, y_{k-1})$ verwendet
- Mithilfe von Extrapolation kann $y_{k + 1}$ somit besser approximiert werden, ohne, dass $f$ oefter ausgewertet werden muss
- Hierbei sind unterscheidliche Methoden moeglich:
$$y_{k + 1} = y_k + \frac{\delta t}{2} \big (3f(t_k, y_k) - f(t_{k - 1}, y_{k - 1}) \big)$$
$$y_{k + 1} = y_{k - 1} + 2\delta t \cdot f(t_k, y_k)$$
- Fuer den ersten Schritt, muss jedoch eine Einschrittmethode verwendet werden
#### Implizites Eulerverfahren
- Um $y_{k + 1}$ zu bestimmen, werden $y_k$, sowie der Differenzenquotient $f(t_{k + 1}, y_{k + 1})$ verwendet
- Hierbei gilt:
$$y_{k + 1} = y_k + \delta t \cdot f(t_{k + 1}, y_{k + 1})$$
## Fehlerverhalten
- Approximationsverfahren werden anhand ihrer Konsistenz und Konvergenz bewertet
#### Konsistenz
- Der maximale Fehler einer einzelnen Approximation ist der lokale Diskretisierungsfehler
- Ein Verfahren ist konsistent, falls der lokale Diskretisierungsfehler gegen 0 geht, falls $\delta t$ gegen 0 geht
#### Konvergenz
- Der maximale Fehler der Summe aller Approximationen ist der globale Diskretisierungsfehler
- Ein Verfahren ist konvergent, falls der globale Diskretisierungsfehler gegen 0 geht, falls $\delta t$ gegen 0 geht
- Ein Verfahren konvergiert genau dann, wenn es konsistent und [[Fliesskommazahlen und Rundung|stabil]] ist
#### Steifheit
- Fuer steife Probleme sind selbst konsistente und konvergente Verfahren teils zu ineffizient, da sie extrem kleine Zeitschritte erfordern