## Relation
- Relationen sind Teilmengen aus Kreuzprodukten unterschiedlicher Werte, die ihre Attribute annehmen koennen
- Tupel sind Elemente einer Relation
- Mithilfe eines Schemas wird das Format einer Relation definiert
#### Schluessel
- Ein Schluesselkandidat ist eine minimale Menge an Attributen, die jedes Tupel eindeutig identifiziert
- Einer der Schluesselkandidaten wird als Primaerschluessel der Relation ausgewaehlt
#### Ableitung aus Entities
- Relationen koennen mithilfe der Entities eines [[Konzeptuelle Modellierung|Entity-Relationship-Modells]] hergeleitet werden
- Hierbei koennen die Attribute des Entities einfach als Attribute der Relation verwendet werden
###### Beispiel
![[Pasted image 20231025112648.png]]
![[Pasted image 20231025112658.png]]
#### Beispiel
![[Pasted image 20231025111701.png]]
## Beziehungen
- Unterschiedliche Beziehungsarten werden auf unterschiedliche Weisen in ein relationales Datenmodell uebersetzt
#### N:M Beziehungen
- Eine zusaetzliche Relation wird erstellt, welche die Schluessel der beiden Relationen speichert, die in einer Beziehung zueinander stehen
- Der Primaerschluessel der Relation setzt sich aus den gespeicherten Schluesseln zusammen
#### 1:N Beziehungen
- Die Relation auf der "N" Seite der Beziehung referenziert die jeweils andere Relation mithilfe eines Fremdschluessels
#### 1:1 Beziehungen
- Eine beliebige Relation referenziert die jeweils andere mithilfe eines Fremdschluessels
#### Beispiel
![[Pasted image 20231025131848.png]]
![[Pasted image 20231025131909.png]]
## Relationale Algebra
- Unterschiedliche Operationen koennen auf Relationen angewandt werden
#### Selektion
- Mithilfe einer Selektion $\sigma$ kann auf einzelne Tupel einer Relation zugegriffen werden
###### Beispiel
![[Pasted image 20231025132134.png]]
#### Projektion
- Mithilfe einer Projektion $\Pi$ kann auf einzelne Attribute einer Relation zugegriffen werden
###### Beispiel
![[Pasted image 20231025132226.png]]
#### Joins
- Zwei Relationen koennen ueber einen join verknuepft werden
- Hierfuer wird mithilfe eines kartesischen Produkts jedes Tupel einer Relation mit jedem Tupel der Anderen verknuepft
- Ueber ein Praedikat wird das Ergebnis gefiltert
###### Outer Joins
- Bei einem outer join werden auch Zeilen inkludiert, die das Praedikat nicht erfuellen
- Dort werden fehlende Werte mit null aufgefuellt
###### Beispiel
![[Pasted image 20231025133039.png]]
![[Pasted image 20231025133222.png]]
## Division
- Es seien $R, S$ Relationen mit den Attributen $\beta, \gamma$, wobei $\gamma \subset \beta$ ist
- Es sei $\overline{R} = \Pi_{\beta \setminus \gamma}(R)$
- Es werden genau die Zeilen aus $\overline{R}$ ausgegeben, deren Gegenstuecke in $R$, $S$ enthalten
#### Beispiel
![[Pasted image 20231025193644.png]]
## Aggregation und Gruppierung
- Tupel einer Relation koennen ausgehend von ihren Attributwerten gruppiert werden
- Bei einer Gruppierung koennen Attribute aggregiert, beispielsweise summiert werden
#### Beispiel
![[Pasted image 20231025192743.png]]
## Tupelkalkuel
- Alternativ zur relationalen Algebra kann das Relationenkalkuel fuer Anfragen verwendet werden
#### Aufbau
- Eine Anfrage im Relationenkalkuel hat die Form $\{t \mid P(t)\}$, wobei $t$ ein Tupel und $P(t)$ eine Formel zur Einschraenkung des Ergebnisses ist
- Eine Formel kann ein Vergleich zwischen Variablen, oder eine Kombination mehrerer Formeln sein
- Eine Formel $P$ kann auf eine Relation $R$ ueber $R(P)$ angewandt werden, um sie zu filtern
#### Beispiel
$$\{s \mid s \in \text{Studenten } \land \forall v \in \text{Vorlesungen}(v.SWS = 4 \Rightarrow \exists h \in \text{hoeren}(h.VorlNr = v.VorlNr \land h.MatrNr = s.MatrNr))\}$$
- Es werden alle Studenten ausgegeben, die an allen vierstuendigen Vorlesungen teilnehmen
## Domaenenkalkuel
- Aehnlich zum Relationenkalkuel koennen auch mithilfe der Domaenenkalkuels, Anfragen erstellt werden
#### Aufbau
- Eine Anfrage im Domaenenkalkuel hat die Form $\{[v_1, ..., v_n] \mid P(v_1, ..., v_n)\}$, wobei $v_i$ Domaenenvariablen und $P$ eine Formel ist
- Domaenenvariablen entsprechen den Attributen der Relationen
#### Beispiel
$$\{[matrNr, sName] \mid \exists s ([matrNr, sName] \in \text{Studenten } \land \exists persNr ([matrNr, persNr] \in \text{pruefen } \land \exists name ([persNr, name] \in \text{Professoren } \land name = \text{"Curie"})))$$
- Es werden alle Matrikelnummern und Namen der Prueflinge von Curie wiedergegeben