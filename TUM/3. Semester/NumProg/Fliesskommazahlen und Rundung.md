## Diskrete und endliche Zahlenmengen
- Zahlenmengen sind in der Regel stetig und unendlich
- Da Rechner nur endliche Zahlenmengen repraesentieren koennen, muessen Ergebnisse approximiert werden
- Rechner koennen sowohl Ganzzahlen, als auch Fliesskommazahlen darstellen
#### Fliesskommazahldarstellung
- Eine Fliesskommazahl wird mithilfe einer Mantisse, eines Exponenten und eines Vorzeichenbits dargestellt
- Der minimale absolute Abstand zweier Fliesskommazahlen variiert und ist groesser, je groesser die Zahlen sind
- Der minimale relative Abstand zwischen zwei Fliesskommazahlen ist immer gleich und wird als die Aufloesung $\varrho$ bezeichnet
## Rundungsprinzip
- Die Menge der Zahlen, die als Fliesskommazahl dargestellt werden kann ist diskret
- Somit kann das Ergebnis einer Addition zweier darstellbarer Zahlen auserhalb dieser Menge liegen
- Ein solches Ergebnis muss mithilfe einer Rundung in den darstellbaren Bereich gebracht werden
#### Rundungsfehler
- Der relative Rundungsfehler $\varepsilon$ einer Fliesskommazahl $x$ wird beschrieben durch:
$$\varepsilon(x) = \frac{\text{rd}(x) - x}{x}$$
- Somit gilt fuer eine gerundete Zahl $x$:
$$\text{rd}(x) = x(1 + \varepsilon)$$
- Aufgrund des Rundungsverhaltens von Fliesskommazahlen ist die Addition nicht assoziativ
## Fliesskommaarithmetik
- Waehrend einer Berechnung mit Fliesskommazahlen koennen sich Rundungsfehler akkumulieren
- Um dies zu verhindern, wird der moegliche Rundungsfehler bei einer Operation mithilfe der Schranke $\tilde{\varepsilon} \in O(\varrho)$ eingegrenzt
## Kondition
- Die Kondition beschreibt, wie sehr die Stoerung $\delta y$ in der Ausgabe von der Stoerung $\delta x$ in der Eingabe beeinflusst wird
- Haben selbst kleine Aenderungen in $\delta x$ grosse Auswirkungen auf $\delta y$, so liegt eine schlechte Kondition vor, andernfalls eine Gute
#### Konditionsnummer
- Je nach Kondition, wird einer Operation eine Konditionsnummer zugeteilt
- Die absolute und relative Konditionsnummern $c_{abs}$  und $c_{rel}$ der Operation $f$ ergeben sich durch:
$$c_{abs} = \frac{f(x + \delta x) - f(x)}{\delta x} = f'(x)$$
$$c_{rel} = \frac{c_{abs} \cdot x}{f(x)}$$
## Stabilitaet
- Da Eingaben stets eine Stoerung $\tilde{x}$ besitzen, gilt jede Loesung $\tilde{y}$ als akzeptables Ergebnis von $p(x)$, falls gilt:
$$\tilde{y} = p(\tilde{x}), \tilde{x} \in \{\tilde{x} 
\mid \forall \tilde{x} \in \mathbb{F}, \exists x, \varepsilon \in \mathbb{R}: |\tilde{x} - x| < \varepsilon\}$$
- Ein Algorithmus ist stabil, falls fuer alle Eingaben innerhalb einer erlaubten Stoerung, akzeptable Ergebnisse geliefert werden 
## Ausloeschung
- Bei einer Subtraktion zweier, gleich grosser Zahlen kann es zu einem grossen Verlust relevanter Stellen und grossen relativen Fehlern kommen
#### Beispiel
- Bereits eine Stoerung der Ordnung $O(10^{-6})$ kann zu grossen relativen Fehlern fuehren:
$$(1000000 + 1) - (999999 - 1) = 3$$