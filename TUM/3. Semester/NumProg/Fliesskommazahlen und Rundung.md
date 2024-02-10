## Diskrete und endliche Zahlenmengen
- Zahlenmengen sind in der Regel stetig und unendlich
- Da Rechner nur endliche Zahlenmengen repraesentieren koennen, muessen Ergebnisse approximiert werden
- Rechner koennen sowohl Ganzzahlen, als auch Fliesskommazahlen darstellen
#### Fliesskommazahldarstellung
- Der minimale absolute Abstand zweier Fliesskommazahlen variiert und ist groesser, je groesser die Zahlen sind
- Der minimale relative Abstand zwischen zwei Fliesskommazahlen ist immer gleich und wird als die Aufloesung $\varrho$ bezeichnet
###### IEEE Standard
- Der IEEE Standard gibt vor, wie eine Fliesskommazahl im Speicher liegt
- Eine Zahl wird durch ein Vorzeichenbit, Exponentenbits, sowie Mantissenbits dargestellt, wobei eine 1 vor dem Komma implizit ist
- Vom dem gespeicherten Exponenten wird stets ein fester BIAS abgezogen
## Rundungsprinzip
- Die Menge der Zahlen, die als Fliesskommazahl dargestellt werden kann ist diskret
- Somit kann das Ergebnis einer Addition zweier darstellbarer Zahlen auserhalb dieser Menge liegen
- Ein solches Ergebnis muss mithilfe einer Rundung in den darstellbaren Bereich gebracht werden
#### Rundungsfehler
- Der relative Rundungsfehler $\varepsilon$ einer Fliesskommazahl $x$ wird beschrieben durch:
$$\varepsilon(x) = \Big | \frac{\text{rd}(x) - x}{x} \Big |$$
- Aufgrund des Rundungsverhaltens von Fliesskommazahlen ist die Addition nicht assoziativ
#### Rundungsverfahren
- Eine Fliesskommazahl wird abgerundet, falls $y | 0x$ gilt und $x$ beliebig ist, oder, falls $y0 | 1x$ gilt und $x$ ausschliesslich aus Nullen besteht
- In allen anderen Faellen wird aufgerundet
#### Maschinengenauigkeit
- Die Maschinengenauigkeit $\epsilon_{MA}$ beschreibt den maximalen relativen Fehler, der bei der Darstellung einer Zahl entstehen kann:
$$\epsilon_{MA} = \Big (\frac12 \Big ) \cdot B^{(1 - M)}$$
- $B$ entspricht hierbei der Zahlenbasis und $M$ der Anzahl der Mantissenbits, inklusive der fuehrenden $1$
## Kondition
- Die Kondition beschreibt, wie sehr die Stoerung $\delta y$ in der Ausgabe von der Stoerung $\delta x$ in der Eingabe beeinflusst wird
- Haben selbst kleine Aenderungen in $\delta x$ grosse Auswirkungen auf $\delta y$, so liegt eine schlechte Kondition vor, andernfalls eine Gute
#### Konditionsnummer
- Je nach Kondition, wird einer Operation eine Konditionsnummer zugeteilt
- Die absolute und relative Konditionsnummern $c_{abs}$  und $c_{rel}$ der Operation $f$ ergeben sich durch:
$$c_{abs} = \frac{f(x + \delta x) - f(x)}{\delta x} = f'(x)$$
$$c_{rel} = \left | \frac{c_{abs} \cdot x}{f(x)} \right |$$
## Stabilitaet
- Eine Loesung $\tilde{y}$ gilt als akzeptables Ergebnis von $p(x)$, falls sie das exakte Ergebnis von $p(\tilde{x})$ ist, wobei sich $\tilde{x}$ kaum von $x$ unterscheidet:
$$\tilde{y} = p(\tilde{x}), \space \space |\tilde{x} - x| < \varepsilon$$
- Ein Algorithmus ist stabil, falls fuer alle Eingaben innerhalb einer erlaubten Stoerung, akzeptable Ergebnisse geliefert werden
- Dies ist nicht der Fall, falls sich Rundungfehler akkumulieren und stark abgewandelte Ergebnisse liefern
- Ist ein Problem schlecht konditioniert, so ist die Stabilitaet eines Algorithmus bedeutungslos
#### Epsilontik
- Um die Stabilitaet eines Algorithmus zu messen, wird in jede Operation ein Fehler $\epsilon_i$ einberechnet
- Der resultierende relative Fehler beschreibt die Stabilitaet des Algorithmus
## Ausloeschung
- Bei einer Subtraktion zweier, gleich grosser Zahlen kann es zu einem grossen Verlust relevanter Stellen und grossen relativen Fehlern kommen
#### Beispiel
- Bereits eine Stoerung der Ordnung $O(10^{-6})$ kann zu grossen relativen Fehlern fuehren:
$$(1000000 + 1) - (999999 - 1) = 3$$